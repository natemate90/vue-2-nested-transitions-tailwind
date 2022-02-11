<template>
    <!-- This example requires Tailwind CSS v2.0+ -->
    <Transition
        :duration="100"
        enter-active-class="transition-all ease-out duration-100"
        enter-class="opacity-0"
        enter-to-class="opacity-100"
        leave-active-class="transition-opacity ease-out duration-100"
        leave-class="opacity-100"
        leave-to-class="opacity-0"
        @before-enter="showContent = true"
    >
        <div
            v-if="open"
            class="fixed z-0 inset-0 overflow-y-auto bg-gray-700 bg-opacity-50"
            aria-labelledby="modal-title"
            role="dialog"
            aria-modal="true"
        >
            <div
                class="
                    flex
                    items-end
                    justify-center
                    min-h-screen
                    pt-4
                    px-4
                    pb-20
                    text-center
                    sm:block sm:p-0
                "
            >
                <!-- This element is to trick the browser into centering the modal contents. -->
                <span
                    class="hidden sm:inline-block sm:align-middle sm:h-screen"
                    aria-hidden="true"
                    >&#8203;</span
                >
                <Transition
                    enter-active-class="transition-all transform ease-out duration-150"
                    enter-class="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
                    enter-to-class="opacity-100 translate-y-0 sm:scale-100"
                    leave-active-class="transition-all transform ease-out duration-150"
                    leave-class="opacity-100 translate-y-0 sm:scale-100"
                    leave-to-class="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
                    @before-leave="$emit('close')"
                >
                    <div
                        v-if="showContent"
                        v-click-outside="close"
                        class="
                            z-100
                            inline-block
                            align-bottom
                            bg-white
                            rounded-lg
                            px-4
                            pt-5
                            pb-4
                            text-left
                            overflow-hidden
                            shadow-xl
                            transform
                            transition-all
                            sm:my-8 sm:align-middle sm:max-w-sm sm:w-full sm:p-6
                        "
                    >
                        <slot />
                    </div>
                </Transition>
            </div>
        </div>
    </Transition>
</template>

<script>
export default {
    name: "Modal",

    props: {
        open: {
            type: Boolean,
            default: false
        }
    },

    data() {
        return {
            showContent: false
        }
    },

    methods: {
        close() {
            this.showContent = false
        }
    }
}
</script>
