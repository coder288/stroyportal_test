<template>
    <div class="header">
        <a href="#" class="header__logo"></a>
        <div class="header__catalog">Каталог</div>
        <div class="header__search-wrapper">
            <i class="header__search-ico"></i>
            <input class="header__search-input" v-model="search" placeholder="Хочу найти...">
            <div class="header__autocomplete" v-if="search.length && autocompleteArr.length">
                <a
                    class="header__autocomplete-item"
                    v-for="item in autocompleteArr"
                    :key="item.id"
                    :href="item.url"
                >{{ item.title }}</a>
            </div>
        </div>
        <div class="header__list header__list--active">Список</div>
        <div class="header__user">A</div>
    </div>
</template>

<script>
    export default {
        name: "Header",
        data() {
            return {
                search: '',
                autocomplete: [
                    {
                        id: '1',
                        title: 'арбуз',
                        url: 'https://yandex.ru'
                    },
                    {
                        id: '2',
                        title: 'авокадо',
                        url: 'https://yandex.ru'
                    },
                    {
                        id: '3',
                        title: 'морковь',
                        url: 'https://yandex.ru'
                    },
                    {
                        id: '4',
                        title: 'кортофель',
                        url: 'https://yandex.ru'
                    },
                    {
                        id: '5',
                        title: 'тыква',
                        url: 'https://yandex.ru'
                    },
                    {
                        id: '6',
                        title: 'кабачок',
                        url: 'https://yandex.ru'
                    },
                    {
                        id: '7',
                        title: 'свекла',
                        url: 'https://yandex.ru'
                    }
                ],
                autocompleteArr: []
            }
        },
        watch: {
            search: function() {
                this.autocompleteArr = this.autocomplete.filter(elem => elem.title.toLowerCase().indexOf(this.search.toLowerCase()) + 1);
            }
        },
        methods: {
            clickHandler(event) {

                if (!event.target.closest('.header__autocomplete')) {
                    this.autocompleteArr = [];
                }
            }
        },
        mounted() {
            document.addEventListener('click', this.clickHandler);
        },
        beforeDestroy() {
            document.removeEventListener('click', this.clickHandler);
        }
    }
</script>

<style scoped lang="scss">
    .header { padding: 0 85px; background: #fff; height: 76px; display: flex; align-items: center; border-bottom: 1px solid #ECEFF1; }
    .header__logo { width: 221px; height: 48px; background: url(i/logo.svg) no-repeat 50%; margin: 0 24px 0 0; }
    .header__catalog { background: #FED83D url(i/menu.svg) no-repeat left 16px top 50%; border-radius: 4px; padding: 8px 18px 8px 45px; font: 600 14px/24px 'open sans'; margin: 0 24px 0 0; cursor: pointer; transition: background-color 150ms; }
    .header__catalog:hover { background-color: #e3be3a; }
    .header__search-wrapper { flex: 1; position: relative; margin: 0 24px 0 0; }
    .header__search-ico { width: 18px; height: 18px; background: url(i/search.svg) no-repeat 50%; position: absolute; right: 11px; top: 0; bottom: 0; margin: auto; }
    .header__search-input { width: 100%; height: 40px; background: #fff; border: 1px solid #ECEFF1; border-radius: 4px; padding: 0 28px 0 14px; color: #708598; font: 400 14px/24px 'open sans'; }
    .header__search-input:focus, .header__search-input:hover { border-color: #09f; }
    .header__list { font: 600 14px/24px 'open sans'; cursor: pointer; margin: 0 24px 0 0; padding: 8px 16px 8px 44px; background: #FAFBFC url(i/list.svg) no-repeat left 14px top 50%; border: 1px solid #ECEFF1; border-radius: 4px; transition: background-color 150ms; }
    .header__list:hover { background-color: #dedfe0; }
    .header__list--active { background-image: url(i/list-active.svg); }
    .header__user { width: 40px; height: 40px; border-radius: 50%; background: #9B51E0; text-align: center; color: #fff; text-transform: uppercase; font: 600 14px/40px 'open sans'; cursor: pointer; transition: background-color 150ms; }
    .header__user:hover { background-color: #8847c4; }
    .header__autocomplete { position: absolute; background: #fff; box-shadow: 0 0 10px 1px rgba(0,0,0,.2); margin: 10px 0 0 0; border-radius: 4px; width: 100%; overflow: hidden; }
    .header__autocomplete-item { display: block; padding: 10px; border-bottom: 1px solid #ccc; font: 400 14px/14px 'open sans'; color: #708598; transition: background-color 150ms; background: #fff; }
    .header__autocomplete-item:last-child { border-bottom: none; }
    .header__autocomplete-item:hover { background: #ffeb87; color: #000; cursor: pointer; }
</style>