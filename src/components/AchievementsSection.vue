<template>
    <section class="achievements">
        <div class="achievements__wrapper wrapper">
            <div class="achievements__info">
                <div class="achievements__head">
                    <h1 class="achievements__title">Мои достижения в</h1>
                    <img src="../assets/icons/strokeStar.svg" alt="decorate icon"
                        class="achievements__icon achievements__icon--sstar">
                    <h1 class="achievements__name">science & education</h1>
                </div>
                <p class="achievements__desc">Список личных достижений (дипломов, сертификатов, справок, публикаций) в
                    научной
                    и образовательной сфере. Собранные данные от сентября 2021 года по нынешний момент.</p>
                <img src="../assets/icons/fillStar.svg" alt="decorate icon"
                    class="achievements__icon achievements__icon--fstar">
                <div class="achievements__settings">
                    <SearchBar :onSearch="onSearch" title="Поиск по названию, описанию и категории" />
                    <SelectBox :content="sortCollection" id="sortSelect" :onSelect="onSelect" title="Сортировка" />
                </div>
                <ul class="achievements__list">
                    <li class="achievements__item case" v-for="item, key in sortedAchievements" :key="key">
                        <img v-if="item.media.type == 'image'"
                            :src="require('../assets/achievements/' + item.media.title)" loading="lazy"
                            alt="image for achievement case" class="case__media">
                        <ul class="case__badges">
                            <li v-for="badge, keybadge in item.badges" :key="keybadge" class="case__badge">
                                <p class="case__badge-title">{{ badge }}</p>
                            </li>
                        </ul>
                        <h2 class="case__title">{{ item.name }}</h2>
                        <p class="case__desc">{{ item.desc }}</p>
                        <div class="case__actions">
                            <a v-if="item.link" :href="item.link" class="case__link" target="_blank">
                                <p class="case__link-text">Перейти</p>
                            </a>
                        </div>
                    </li>

                </ul>
            </div>
        </div>
    </section>
</template>

<script>
import Fuse from 'fuse.js';
import SearchBar from './SearchBar.vue';
import debounce from 'lodash/debounce';
import SelectBox from './SelectBox.vue';

export default {
    name: 'AchievementsSection',
    data() {
        return {
            fuse: null,
            filteredAchievements: [],
            selectedSort: "dateUp",
            achievements: [
                {
                    name: 'Научная статья «Разработка мобильного приложениядля отслеживания качества воздуха в условиях городской среды»',
                    desc: 'Конференция «ПРЕДОТВРАЩЕНИЕ. СПАСЕНИЕ. ПОМОЩЬ»  Академия гражданской защиты Министерства Российской Федерации по делам гражданской обороны, чрезвычайным ситуациям и ликвидации последствий стихийных бедствий имени генерал-лейтенанта Д.И. Михайлика',
                    date: '01.03.2023',
                    importance: 1,
                    media: {
                        type: 'image',
                        title: 'a1.jpg'
                    },
                    link: 'https://elibrary.ru/item.asp?id=50736683',
                    badges: ['научная статья', 'РИНЦ', 'конференция'],
                },
                {
                    name: 'Успешное прохождение ДПО «Нейросетевые технологии» с ассементом университета Иннополис и практикой от компании ООО «Заря»',
                    date: '13.09.2024',
                    importance: 2,
                    media: {
                        type: 'image',
                        title: 'e1.jpg'
                    },
                    link: 'https://s3-api.unionepro.ru/basebucket/66e40304adc1ce89b1ffd972.pdf?s3token=1c64ee5b98f93b0d08558f8d878fda82dcb7c2bb8e7a4f1388d621249200cc51',
                    badges: ['ДПО', 'обучение', 'практика', 'ИИ'],
                },
                {
                    name: 'Научный проект «Сервис для мониторинга концентрации аллергенов в городской среде»',
                    desc: '11-й Международной молодежной научной конференции «ЮНОСТЬ И ЗНАНИЯ - ГАРАНТИЯ УСПЕХА-2024», которая проходила 19-20 сентября 2024 года в г.Курске',
                    date: '19.09.2024',
                    importance: 2,
                    media: {
                        type: 'image',
                        title: 'd4.png'
                    },
                    badges: ['конференция', '3 место'],
                },
                {
                    name: 'Разработка веб-сайта для организации и контроля физической активности в эпоху цифровой трансформации общества',
                    desc: 'VI Международный научный Форум профессорско-преподавательского состава и молодых ученых «ЦИФРОВЫЕ ТЕХНОЛОГИИ: НАУКА, ОБРАЗОВАНИЕ, ИННОВАЦИИ»',
                    date: '27.11.2023',
                    importance: 4,
                    media: {
                        type: 'image',
                        title: 'd1.jpg'
                    },
                    badges: ['конференция', '2 место'],
                },
                {
                    name: 'Лучший научный проект',
                    desc: 'XIII Международной научно-практической конференции докторантов, магистрантов и студентов «МОЛОДЕЖЬ, НАУКА, ОБРАЗОВАНИЕ: АКТУАЛЬНЫЕ ВОПРОСЫ, ДОСТИЖЕНИЯ И ИННОВАЦИИ»',
                    date: '29.09.2022',
                    importance: 6,
                    media: {
                        type: 'image',
                        title: 'd2.jpg'
                    },
                    badges: ['конференция', '1 место', 'Казахстан'],
                },
                {
                    name: 'Победитель III Всероссийского правового кейс-чемпионата «Эксперт+»',
                    desc: 'Институт законодательства и сравнительного правоведения при Правительстве РФ',
                    date: '08.10.2022',
                    importance: 3,
                    media: {
                        type: 'image',
                        title: 'd3.jpeg'
                    },
                    badges: ['конференция', '3 место'],
                },
                {
                    name: 'Создание единой информационной системы мониторинга загрязнения атмосферного воздуха на территории города Киров',
                    desc: 'XVII Ежегодная Международная научно-практическая сессия «Неделя науки молодёжи СВАО г.Москвы» в секции «Цифровые технологии в экономике и социальной сфере»',
                    date: '30.04.2022',
                    importance: 5,
                    media: {
                        type: 'image',
                        title: 'd5.jpg'
                    },
                    badges: ['конференция', '1 место', 'гран при'],
                },
                {
                    name: 'Проект на тему «Разработка приложения «Daily Kirov» как фактор развития цифровой экономики в рамках стратегии цифровой трансформации»',
                    desc: 'XIII Международная конференция профессорско-преподавательского состава и молодых ученых «ИНФОРМАЦИОННЫЕ ТЕХНОЛОГИИ, СИСТЕМЫ И ВОПРОСЫ КИБЕРБЕЗОПАСНОСТИ»',
                    date: '24.06.2022',
                    importance: 6,
                    media: {
                        type: 'image',
                        title: 'd6.jpg'
                    },
                    badges: ['конференция', '1 место'],
                },
                {
                    name: 'Проект на тему "Разработка автоматизированной информационной системы «Сбор, анализ и прогноз экологической обстановки в городе»"',
                    desc: 'III Международный конкурс научных и научно-практических работ «ІТ ПРОЕКТЫ «ЦИФРОВАЯ ТРАНСФОРМАЦИЯ»',
                    date: '12.04.2022',
                    importance: 6,
                    media: {
                        type: 'image',
                        title: 'd7.png'
                    },
                    badges: ['конференция', '1 место'],
                },
                {
                    name: 'Победа с разработкой «Мобильное приложение мониторинга экологической обстановки и эко-карты города Киров Daily Киров»',
                    desc: 'Международный конкурс научно-практических работ и проектов в рамках Международной конференции «Цифровая трансформация общества: тенденции и перспективы»',
                    date: '19.11.2021',
                    importance: 7,
                    media: {
                        type: 'image',
                        title: 'd8.jpeg'
                    },
                    badges: ['конференция', '1 место'],
                },
                {
                    name: 'Победа за лучшую научную работу с темой «Разработка мобильного приложения, предназначенного для сбора и анализа данных об экологическом состоянии атмосферы города на примере создания эко-карты»',
                    desc: 'V Международный конкурс на лучшую научную работу для аспирантов, студентов и школьников "ARS SACRA AUDIT"',
                    date: '13.12.2021',
                    importance: 6,
                    media: {
                        type: 'image',
                        title: 'd9.png'
                    },
                    badges: ['конференция', '3 место'],
                },
                {
                    name: 'Проект на тему "Проектирование автоматизированной информационной системы: «Прогноз экологической обстановки в городе»"',
                    desc: 'Всероссийская конференция профессорско-преподавательского состава и молодых ученых «ЦИФРОВОЙ МИР: ГЛОБАЛЬНЫЕ ВЫЗОВЫ И ТРЕНДЫ»',
                    date: '30.10.2022',
                    importance: 6,
                    media: {
                        type: 'image',
                        title: 'd10.png'
                    },
                    badges: ['конференция', '1 место'],
                },
            ],
            sortCollection: [
                { name: "Сначала новые", value: "dateUp" },
                { name: "Сначала старые", value: "dateDown" },
                { name: "По важности", value: "importance" }
            ]
        }
    },
    mounted() {
        const options = {
            keys: ['name', 'desc', 'badges'],
            includeScore: true,
            threshold: 0.3,
        };
        this.fuse = new Fuse(this.achievements, options);
        this.filteredAchievements = this.achievements;
    },
    watch: {
        searchQuery() {
            this.filteredAchievements = this.fuseSearch;
        },
    },
    computed: {
        fuseSearch() {
            if (this.searchQuery) {
                const result = this.fuse.search(this.searchQuery);
                return result.map(res => res.item);
            }
            return this.achievements;
        },
        sortedAchievements() {
            let achievements = this.filteredAchievements;
            if (this.selectedSort) {
                const parseDate = (dateStr) => {
                    const [day, month, year] = dateStr.split('.').map(Number);
                    return new Date(year, month - 1, day);
                };

                if (this.selectedSort === 'dateUp') {
                    achievements.sort((a, b) => parseDate(b.date) - parseDate(a.date));
                } else if (this.selectedSort === 'dateDown') {
                    achievements.sort((a, b) => parseDate(a.date) - parseDate(b.date));
                } else if (this.selectedSort === 'importance') {
                    achievements.sort((a, b) => a.importance - b.importance);
                }
            }
            return achievements;
        }
    },
    methods: {
        onSearch: debounce(function (query) {
            if (query && typeof query === 'string') {
                this.filteredAchievements = this.fuse.search(query).map(res => res.item);
            } else {

                this.filteredAchievements = this.achievements;
            }
        }, 300),
        onSelect: debounce(function (ctx) {
            console.log(ctx)
            this.selectedSort = ctx;
        }, 400)
    },
    components: { SearchBar, SelectBox },

}
</script>

<style lang="scss" scoped>
.achievements__wrapper {
    border-radius: 40px;
    padding-top: 40px;
    padding-bottom: 40px;
    background-color: white;
    z-index: -2;
}

.achievements__info {
    position: relative;
    display: flex;
    justify-content: space-between;
    flex-flow: row;
    flex-wrap: wrap;
    gap: 40px;
    height: min-content;
    overflow: visible;
    padding: 0px;
}

.achievements__head {
    position: relative;
    place-content: flex-start;
    align-items: flex-start;
    display: flex;
    flex: 0 0 auto;
    flex-flow: column;
    gap: 0px;
    height: min-content;
    overflow: hidden;
    padding: 10px 28px;
}

.achievements__title {
    font-family: 'Neue Machina';
    font-size: 60px;
    text-align: center;
    color: black;
    padding: 0;
    margin: 0;
}

.achievements__name {
    font-family: 'PP Migra Italic Extrabold Italic', serif;
    color: rgb(49, 189, 214);
    font-size: 60px;
    text-align: center;
    width: fit-content;
    padding: 0;
    margin: -20px 0 -20px;
    height: fit-content;
}

.achievements__desc {
    color: black;
    font-family: 'PP Neue Machina Regular';
    max-width: 45%;
    font-size: 18px;
    text-align: left;
    line-height: 1.5;
    margin-top: 30px;
}

.achievements__icon {
    position: absolute;

    &--sstar {
        right: 40px;
        bottom: 0px;
        transform: rotate(-30deg);
    }

    &--fstar {
        right: 20px;
        bottom: -20px;
        transform: rotate(-30deg);
    }
}

.achievements__settings {
    padding: 0 32px;
    margin: 0;
    display: flex;
    flex-wrap: wrap;
    column-gap: 40px;
    align-items: center;
}

.achievements__list {
    list-style: none;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(360px, 1fr));
    flex-wrap: wrap;
    column-gap: 0px;
    row-gap: 0px;
    justify-content: center;
    padding: 0;
    margin: 0;
}

.achievements__item {
    z-index: 0;
    // max-width: 720px;
    // min-width: 560px;
    padding: 26px 32px;
    font-family: 'PP Neue Machina Regular';
    color: black;
}

.case__title {
    font-size: 18px;
    font-weight: 800;
    margin: 18px 0 6px;
}

.case__desc {
    font-size: 14px;
    line-height: 1.5;
    text-align: justify;
}

.case__media {
    width: 100%;
    border-radius: 20px;
    object-fit: cover;
}

.case__actions {
    place-content: center;
    display: flex;
    gap: 10px;
    align-items: center;
}

.case__link {
    cursor: pointer;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    text-decoration: none;
    padding: 12px 20px;
    font-family: 'PP Neue Machina Regular';
    border: 1.4px solid #020202;
    color: #020202;
    background-color: transparent;
    border-radius: 40px;
    line-height: 1;
    font-size: 16px;
    transition: all .5s;
    margin: 10px;

    &:hover {
        color: white;
        background-color: #020202;
        border: 1px solid transparent;

        & .case__follow {
            filter: invert(100%);
        }
    }

    &--rep {
        padding: 4px;
        border-radius: 48px;
        width: 54.4px;
        aspect-ratio: 1;

        border: none;

        & .case__follow {
            margin: 0;
            padding: 0;
            width: 40px;

        }
    }
}

.case__link-text {
    padding: 0;
    margin: 0;
}

@media screen and (max-width: 1080px) {
    .achievements__desc {
        color: black;
        font-family: 'PP Neue Machina Regular';
        max-width: 100%;
        font-size: 20px;
        padding: 0 28px;
        margin-top: 10px;

    }
}

@media screen and (max-width: 768px) {
    .achievements__title {
        max-width: 100%;
        font-size: 42px;
        padding-bottom: 10px;
    }

    .achievements__name {
        max-width: 100%;
        font-size: 50px;
    }

    .achievements__desc {
        max-width: 100%;
        font-size: 18px;
    }

    .achievements__icon--sstar {
        right: 0px;
        bottom: 20px;
        transform: rotate(-30deg) scale(0.4)
    }

    .case__title {
        font-size: 22px;
    }

    .case__desc {
        font-size: 16px;
        line-height: 1.4;
        padding: 0 20px;
    }

    .case__badge {
        border-radius: 60px;
    }
}

@media screen and (max-width: 560px) {

    .achievements__name {
        font-size: 38px;
        margin-top: 0px;
    }

    .achievements__title {
        font-size: 32px;
        padding: 0;
    }

    .achievements__icon--sstar {
        width: 6em;
        top: 30px;
        right: 3px;
        z-index: 5;
        transform: scale(1.2) rotate(60deg);
    }

    .achievements__desc {
        font-size: 16px;
    }

    .case__title {
        font-size: 20px;
    }

    .case__desc {
        font-size: 14px;
        line-height: 1.4;
    }

    .achievements__list {
        list-style: none;
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
        flex-wrap: wrap;
        column-gap: 20px;
        row-gap: 20px;
        justify-content: center;
        padding: 0;
        margin: 0;
    }

    .achievements__item {
        padding: 0;
    }

    .case__badge-title {
        font-weight: 600;
        font-size: 12px;
        margin: 0;
    }
}

.case__badges {
    list-style: none;
    display: flex;
    gap: 8px;
    align-items: center;
    margin: 8px auto 12px;
    padding: 0;
    flex-wrap: wrap;
}

.case__badge {
    border-radius: 60px;
    border: 1.4px solid rgb(73, 73, 73);
    padding: 4px 10px;
    opacity: 0.6;
}

.case__badge-title {
    font-weight: 400;
    font-size: 16px;
    font-family: Helvetica, Arial, sans-serif;

    margin: 0;
}
</style>