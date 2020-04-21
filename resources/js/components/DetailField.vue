<template>
    <panel-item :field="field">
        <div slot="value">
            <div class="flex flex-wrap items-center -mx-3">
                <div v-for="image in field.value" :key="image.id" class="px-3 w-1/3 min-h-24">
                    <media class="flex items-center border border-40 bg-20" :media="image"></media>
                </div>
            </div>
        </div>
    </panel-item>
</template>

<script>
    import Media from './Media.vue';

    export default {
        props: ['resource', 'resourceName', 'resourceId', 'field'],
        components: {
            Media
        },
    }
</script>
