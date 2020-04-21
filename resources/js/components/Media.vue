<template>
    <div class="relative">
        <img :src="url" :alt="media.name" class="max-w-full max-h-full">
        <div class="bg-80 pin-b w-full absolute flex justify-between p-2">
            <a :href="url" class="text-20 hover:text-40 no-underline" target="_blank" data-lightbox="image-1">+</a>
            <p class="text-20 hover:text-40">{{ size }}</p>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['media'],
        computed: {
            url() {
                if(typeof this.media !== 'undefined' && this.media.disk === 'public') {
                    return '/storage/' + this.media.id + '/' + this.media.file_name;
                }
            },
            size() {
                let size = this.media.size;
                let units = ['B', 'KB', 'MB', 'GB', 'TB'];

                if (size === 0) {
                    return '0 ' + units[1];
                }

                let i;
                for (i = 0; size > 1024; i++) {
                    size /= 1024;
                }

                return _.round(size, 2) + ' ' + units[i];
            }
        }
    }
</script>
