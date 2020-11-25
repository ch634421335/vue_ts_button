<template>
    <button
        class="uiBtn"
        @click="onClickButton"
        :class="{
            uiBtnLarge: large,
            uiBtnSmall: small,
            uiBtnXsmall: xsmall,
            uiBtnXlarge: xlarge,
            uiBtnTile: tile,
            uiBtnRounded: rounded,
            uiBtnCircle: circle,
            uiBtnDisabled: disabled,
        }"
        :style="
            `
            --corlor-tint:${TintColor}
        `
        "
    >
        <slot>Button</slot>
    </button>
</template>

<script lang="ts">
import { Component, Vue, Emit, Prop } from "vue-property-decorator";

@Component
export default class UIButton extends Vue {
    @Prop(Boolean) private large: boolean | undefined;
    @Prop(Boolean) private xsmall: boolean | undefined;
    @Prop(Boolean) private small: boolean | undefined;
    @Prop(Boolean) private xlarge: boolean | undefined;
    @Prop(Boolean) private tile: boolean | undefined;
    @Prop(Boolean) private rounded: boolean | undefined;
    @Prop(Boolean) private circle: boolean | undefined;
    @Prop(Boolean) private disabled: boolean | undefined;
    @Prop(String) private color: string | undefined;

    @Emit("click") private emitClickEvent(event: MouseEvent) {}

    private get TintColor() {
        if (this.color) return this.color;
        else return "#2D8CF0";
    }
    private mounted() {}
    private onClickButton(event: MouseEvent) {
        if (!this.disabled) {
            this.emitClickEvent(event);
        }
    }
}
</script>

<style lang="stylus" scope>
resize(minWidth,height ,paddingLR ,fontSize)
    min-width minWidth
    height height
    padding 0 paddingLR
    font-size fontSize
    &.uiBtnRounded,&.uiBtnCircle
        border-radius (@height / 2)
    &.uiBtnCircle
        width @height
        min-width 0
        padding 0
.uiBtn
    resize(64px,36px,16px,0.875rem)
    border 0 solid black
    border-radius 4px
    color #17233D
    background-color var(--corlor-tint)
    font-weight 500
    letter-spacing 0.09em
    cursor pointer
    user-select none
    outline none
    &:hover
        filter brightness(120%)
    &:active
        filter brightness(80%)
    &.uiBtnXsmall
        resize(36px,20px,9px,0.625rem)
    &.uiBtnSmall
        resize(50px,28px,12px,0.75rem)
    &.uiBtnLarge
        resize(78px,44px,19px,0.875rem)
    &.uiBtnXlarge
        resize(92px,52px,23px,1rem)
    &.uiBtnTile
        border-radius 0
    &.uiBtnDisabled
        background-color #f5f5f5
        color #c5c8ce
        cursor not-allowed
</style>
