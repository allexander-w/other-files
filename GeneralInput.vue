<template>
    <div class="general-input">
            <input type="text" @focus='onFocus' @blur='onBlur' class="general-input-self" v-model='innerModel'>
            <p class="general-input-placeholder" :class='{"active-placeholder": innerModel}' v-bind="classKey">
                {{placeholder}}
            </p>
            <div class="icon"></div>
    </div>
</template>

<script>

export default {
    props: {
        placeholder: {
            type: String,
            default: () => 'Placeholder text'
        },
        vModel: {
            type: String,
            default: () => ''
        },
        numberKey: {
            type: Number,
            default: () => 1
        }
    },
    data: () => ({
       innerModel: '',          
        
    }),
    computed: {
      classKey(){
          return {"data-key": `input${this.numberKey}`} 
      }  
    },
    watch: {
        innerModel() {
            this.$emit('vModel', this.innerModel)
        }
    },
    methods: {
        onFocus() {
            const placeholder = document.querySelectorAll('.general-input-placeholder')
            placeholder.forEach(item => {
                if(item.getAttribute('data-key') === `input${this.numberKey}`){
                    item.classList.add('active-placeholder')
                }
            })
            
        },
        onBlur() {
            if (this.innerModel) {
                return
            }
            const placeholder = document.querySelectorAll('.general-input-placeholder')
            placeholder.forEach(item => {
                if(item.getAttribute('data-key') === `input${this.numberKey}`){
                    item.classList.remove('active-placeholder')
                }
            })
        }
    },
    mounted() {
        this.innerModel = this.vModel
    }
}
</script>

<style lang="scss" scoped>
.icon {
    width: 24px;
    height: 24px;
    background-color: rgba(grey, 0.15);
}

.general-input {
    margin: 12px 0;
    height: 56px;
    border: 1px solid rgba(#0E6CDD, .2);
    border-radius: 5px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    padding: 0 24px;
    position: relative;
    background-color: #fff;

    &-placeholder {
        transform: translate(0,0);
        position: absolute;
        left: 25px;
        font-size: 16px;
        color: rgba(#005CCC, .5);
        transition: .3s ease;
        z-index: 2;
    }
    &:focus-within {
        border: 1px solid rgba(#0E6CDD, .5);
    }

    &-self {
        border: none;
        width: calc(100% - 24px);
        outline: none;
        font-size: 16px;
        color: #333333;
    }
}
.active-placeholder {
    transform: translate(0, -30px);
    padding: 0 8px;
    margin: 0 -8px;
    font-size: 14px;
    z-index: 4;
    color: #005CCC;
    background-color: #fff;
}

</style>