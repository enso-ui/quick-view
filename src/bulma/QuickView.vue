<template>
    <teleport to="body">
        <slide enter="right"
            leave="right"
            @after-leave="emitClose">
            <div class="quick-view-wrapper columns is-justify-content-flex-end"
                v-show="visible">
                <div class="column"
                    :class="$attrs.class">
                    <div class="box quick-view">
                        <a class="delete is-pulled-right"
                            @click="close"/>
                        <slot/>
                    </div>
                </div>
            </div>
        </slide>
    </teleport>
</template>

<script>
import { Slide } from '@enso-ui/transitions';

export default {
    name: 'QuickView',

    components: { Slide },

    inheritAttrs: false,

    data: () => ({
        closeTimer: null,
        closed: false,
        visible: true,
    }),

    emits: ['close'],

    mounted() {
        window.addEventListener('keydown', this.closeOnEscape);
    },

    beforeUnmount() {
        clearTimeout(this.closeTimer);
        window.removeEventListener('keydown', this.closeOnEscape);
    },

    methods: {
        close() {
            if (this.closed) {
                return;
            }

            this.visible = false;
            this.closeTimer = setTimeout(this.emitClose, 350);
        },
        closeOnEscape({ key }) {
            if (key === 'Escape') {
                this.close();
            }
        },
        emitClose() {
            if (this.closed) {
                return;
            }

            this.closed = true;
            clearTimeout(this.closeTimer);
            this.closeTimer = null;
            this.$emit('close');
        },
    },
};
</script>

<style lang="scss">
    .quick-view-wrapper.columns {
        position: fixed;
        inset: 0;
        z-index: 1001;
        pointer-events: none;

        > .column {
            height: 100%;
            pointer-events: none;
        }

        .quick-view.box {
            height: 100vh;
            border-radius: 0;
            position: relative;
            width: 100%;
            display: block;
            pointer-events: auto;
    
            .delete {
                top: 1em;
                right: 1em;
                position: absolute;
                z-index: 2;
            }
        }
    }
</style>
