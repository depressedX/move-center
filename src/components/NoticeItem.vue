<template>
    <div class="notice-item">
        <div class="date">
            <div class="left">
                <div class="month">{{getMonthEngWord(month)}}</div>
                <div class="year">{{year}}</div>
            </div>
            <div class="right day">{{new Date(date).getDay()}}</div>
        </div>
        <div class="seprate"></div>
        <router-link class="title" :to="link">{{title}}</router-link>
    </div>
</template>

<script>
    import {dateUtils} from "../util";

    export default {
        name: "NoticeItem",
        props: {
            date: String,
            title: String,
            link: {
                default: ''
            }
        },
        computed: {
            month() {
                return this.date.split('-')[1] + 1
            },
            year() {
                return this.date.split('-')[0]
            }
        },
        methods: {
            getMonthEngWord: dateUtils.getMonthEngWord,
        }
    }
</script>
<style scoped>
    .notice-item {
        display: flex;
        flex-wrap: nowrap;
        align-items: center;
    }

    .notice-item .date {
        width: 5em;
        flex-shrink: 0;
        font-size: .7em;
        line-height: 1;
        display: flex;
        justify-content: center;
        flex-wrap: nowrap;
    }

    .notice-item .date .left {
        text-align: right;
        font-size: .5em;
    }

    .notice-item .date .month {
        color: black;
    }

    .notice-item .date .year {
        color: rgb(141, 141, 141);
    }

    .notice-item .date .day {
        color: rgb(20, 68, 131);
        font-weight: bold;

    }

    .notice-item .date .right {
        text-align: left;
        font-size: 2em;
    }

    .notice-item .seprate {
        width: 2px;
        height: 1.5em;
        margin: 0 2em;
        flex-shrink: 0;
        background-color: gray;
    }

    .notice-item .title {
        flex-grow: 1;
        color: #474747;
    }
</style>