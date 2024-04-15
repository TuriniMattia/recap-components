<template>
    <div>
        {{ pippo }}
    </div>
</template>

<script>
export default {
    setup() {
        props: {
            pippo: String;
            pluto: Number;
        }

        return {}
    }
}
</script>

<style lang="scss" scoped></style>