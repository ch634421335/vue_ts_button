<template>
    <div class="root-home">
        <div class="btnContainer">
            <UIButton
                @click="onClick"
                :tile="tile"
                :rounded="rounded"
                :circle="circle"
                :xlarge="xlarge"
                :xsmall="xsmall"
                :small="small"
                :large="large"
                :disabled="disabled"
                >1</UIButton
            >
        </div>
        <div class="btnGroup">
            <UIButton class="btn" @click="resize('xsmall')">超小</UIButton>
            <UIButton class="btn" @click="resize('small')">小</UIButton>
            <UIButton class="btn" @click="resize('normal')">正常</UIButton>
            <UIButton class="btn" @click="resize('large')">大</UIButton>
            <UIButton class="btn" @click="resize('xlarge')">超大</UIButton>
        </div>
        <div class="btnGroup">
            <UIButton class="btn" @click="changeRadius('tile')">矩形</UIButton>
            <UIButton class="btn" @click="changeRadius('normal')"
                >正常</UIButton
            >
            <UIButton class="btn" @click="changeRadius('rounded')"
                >半圆</UIButton
            >
            <UIButton class="btn" @click="changeRadius('circle')">圆</UIButton>
        </div>
        <div class="btnGroup">
            <UIButton class="btn" @click="changeDisabled()">禁用</UIButton>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import UIButton from "@/components/UiKit/UIButton.vue";
@Component({
    components: {
        UIButton,
    },
})
export default class Home extends Vue {
    private xlarge: boolean = false;
    private xsmall: boolean = false;
    private small: boolean = false;
    private large: boolean = false;

    private tile: boolean = false;
    private rounded: boolean = false;
    private circle: boolean = false;

    private disabled: boolean = false;
    private resize(name: string) {
        switch (name) {
            case "xsmall":
                this.xsmall = true;
                this.small = false;
                this.large = false;
                this.xlarge = false;
                break;
            case "small":
                this.xsmall = false;
                this.small = true;
                this.large = false;
                this.xlarge = false;
                break;
            case "normal":
                this.xsmall = false;
                this.small = false;
                this.large = false;
                this.xlarge = false;
                break;
            case "large":
                this.xsmall = false;
                this.small = false;
                this.large = true;
                this.xlarge = false;
                break;
            case "xlarge":
                this.xsmall = false;
                this.small = false;
                this.large = false;
                this.xlarge = true;
                break;
        }
    }
    private changeRadius(name: string) {
        switch (name) {
            case "tile":
                this.tile = true;
                this.rounded = false;
                this.circle = false;
                break;
            case "normal":
                this.tile = false;
                this.rounded = false;
                this.circle = false;
                break;
            case "rounded":
                this.rounded = true;
                this.tile = false;
                this.circle = false;
                break;
            case "circle":
                this.circle = true;
                this.tile = false;
                this.rounded = false;
                break;
        }
    }
    private changeDisabled() {
        this.disabled = !this.disabled;
    }

    private onClick(event: MouseEvent) {
        console.log(event);
    }
}
</script>

<style lang="stylus" scope>
.btnContainer
    width 480px
    height 160px
    display flex
    justify-content center
    align-items center
.btn
    margin 6px
</style>
