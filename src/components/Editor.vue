<template>
    <div id="editor">
        <nav>
            <ol>
                <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active: currentTab === i}" v-on:click="currentTab = i">
                    <svg class="icon" aria-hidden="true">
                        <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
                    </svg>
                </li>
            </ol>
        </nav>
        <ol class="panes">
            <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active: currentTab === i}">
                Tab {{i+1}}
            </li>
        </ol>
    </div>
</template>

<script>
export default {
    data() {
        return {
            currentTab: 0,
            icons: ['identity', 'work', 'book', 'project', 'trophy', '3-copy']
        }
    }
}
</script>


<style lang="scss">
#editor {
    border: 1px solid black;
    min-height: 100px;
    display: flex;
    >nav {
        background: black;
        width: 5em;
        >ol>li {
            padding: 8px 0;
            text-align: center;
            >.icon {
                fill: white;
            }
            &.active {
                background: white;
                >.icon {
                    fill: black;
                }
            }
        }
    }
    .panes {
        >li {
            display: none;
            &.active {
                display: block;
            }
        }
    }
}
</style>
