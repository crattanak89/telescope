<script type="text/ecmascript-6">
    import _ from "lodash"

    export default {
        props: ['trace'],

        /**
         * The component's data.
         */
        data() {
            return {
                minimumLines: 5,
                showAll: false,
            };
        },

        computed: {
            lines(){
                return this.showAll ? _.take(this.trace, 1000) : _.take(this.trace, this.minimumLines);
            }
        }
    }
</script>

<template>
    <div class="table-responsive">
        <table class="table mb-0">
            <tbody>
            <tr v-for="line in lines">
                <td class="card-bg-secondary">{{line.file}}:{{line.line}}</td>
            </tr>

            <tr v-if="! showAll">
                <td class="card-bg-secondary"><a href="*" v-on:click.prevent="showAll = true">Show All</a></td>
            </tr>
            </tbody>
        </table>
    </div>
</template>

<style scoped>

</style>