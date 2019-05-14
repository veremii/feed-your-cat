<template>
        <Background :id="model.id" @mouseleave="enableHover($event)" ref="container" :class="{'card-container card-default':true,'card-selected': selected, 'card-disabled': disabled}">
            <div @mouseleave="enableHover($event)" @click="selectionHandler($event)" xmlns="http://www.w3.org/1999/xhtml" class="card-main">
                <div class="card__head">
                    <div class="card__subheader">
                        {{model.subheader || 'Сказочное заморское яство'}}
                    </div>
                    <div class="card__product-name">
                        {{model.productName || 'Нямушка'}}
                    </div>
                    <div class="card__taste">
                        {{model.taste}}
                    </div>
                    <div class="card__gift" v-html="model.gift">

                    </div>
                </div>
                <div class="card__qty">
                    <div class="card__qty-text">
                        <span class="card__qty-value">{{model.qty}}</span>
                        <span class="card__qty-measurement">кг</span>
                    </div>
                </div>
                <div class="card__footer">
                    <span v-if="!selected && !disabled" class="buy">Чего сидишь? Порадуй котэ, <a href="" @click.prevent.stop="selectionHandler()">купи.</a></span>
                    <span v-if="selected && !disabled" class="buy">{{model.description}}</span>
                    <span v-if="disabled" class="buy">Печалька, {{model.taste}} закончился.</span>
                </div>
            </div>
        </Background>
</template>

<script>
    import Background from './cat-background'
    export default {
        name: "Card",
        components: {Background},
        props: {
            model: {

            }
        },
        data(){
            return {
                selected: false,
                disabled: false,
                colors: {
                    default: '#1698D9',
                    defaultHover: '#2EA8E6',
                    selected: '#D91667',
                    selectedHover: '#E52E7A',
                    disabled: '#B3B3B3'
                }
            }
        },
        methods: {
            disabledHandler(){
                if (this.model.id === 2){
                    this.disabled = true;
                }
            },
            selectionHandler(){
                this.selected = !this.selected;
                if (this.selected){
                    this.$emit('select', this.model.id)

                } else {
                    this.$emit('select', this.model.id)
                }
                this.$forceUpdate();
            },
            enableHover(){
                document.getElementById(`${this.model.id}`).classList.add('card__hoverable');
            }
        },
        mounted() {
            this.disabledHandler()
        }
    }
</script>

<style scoped>

</style>