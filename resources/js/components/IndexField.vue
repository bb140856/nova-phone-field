<template>
    <div :class="`text-${field.textAlign}`">
        <template v-if="hasValue">
            <a :href="`tel:+${unmaskedValue}`" class="no-underline dim text-primary whitespace-no-wrap"> {{ field.value }} </a>
        </template>
        <p v-else>&mdash;</p>
    </div>
</template>

<script>
export default {
    props: ['resourceName', 'field'],
    computed: {
        unmaskedValue() {
            return this.field.value ? this.field.value.replace(/\D/g, '') : '';
        },
        hasValue() {
            return this.field.value !== null
        },
    }
};
</script>
