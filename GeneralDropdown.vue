<template>
    <div class="general-dropdown">
            <p class="general-dropdown-self"> Выбор </p>
            <p class="general-dropdown-placeholder">
                placeholder
            </p>
            <div class="icon"></div>
            
            <div class="general-dropdown-body">
                <div class="general-dropdown-body-item">
                    ITEM1
                </div>
            </div>
    </div>
</template>

<script>

export default {
    props: {
        items: {
            type: Array,
            default: () => []
        }
    }
    
}
</script>

<style lang="scss" scoped>
.icon {
    width: 24px;
    height: 24px;
    background-color: rgba(grey, 0.15);
}

.general-dropdown {
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

    &-body {
        position: absolute;
        background: #FFFFFF;
        box-shadow: 0px 0px 40px rgba(51, 51, 51, 0.08);
        border-radius: 5px;
        width: inherit;
        top: calc(56px + 8px);
        left: 0;
        min-height: 56px;
        padding: 8px;
        
        &-item {
            height: 40px;
            display: flex;
            align-items: center;
            border-radius: 5px;
            transition: .5s;
            padding: 0 16px;

            &:hover {
                background: rgba(#0E6CDD, .06);
            }
        }
    }
    &-placeholder {
        position: absolute;
        left: 25px;
        transform: translate(0, -30px);
        padding: 0 8px;
        margin: 0 -8px;
        font-size: 14px;
        z-index: 4;
        color: #005CCC;
        background-color: #fff;
    }
}

</style>