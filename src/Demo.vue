<template>
  <div>
    <functional-calendar
      dateFormat="mm/dd/yyyy"
      :isAutoCloseable="true"
      :change-month-function="true"
      :change-year-function="true"
      :is-modal="true"
      :is-date-range="true"
      :can-clear-range="true"
      :is-dark="true"
      v-model="rangesData"
      :is-multiple-date-range="false"
    >
      <template v-slot:cleaner>
        <button>
          Clear
        </button>
      </template>
    </functional-calendar>

    <div class="console" style="color:white;margin:2em;">
      {{ JSON.stringify(rangesData) }}
    </div>

    <FunctionalCalendar
      class="demo-calendar dateRangeInputs"
      ref="demoCalendar1"
      v-model="demoCalendar1"
      dateFormat="mm/dd/yyyy"
      :is-modal="true"
      :is-date-range="true"
      :is-multiple="true"
      :isLayoutExpandable="true"
      :calendars-count="4"
      :isSeparately="true"
      :change-month-function="true"
      :change-year-function="true"
      arrowsPosition="space-between"
    >
      <template v-slot:dateRangeInputs="props">
        <label for="check-in">
          <svg
            width="21"
            height="23"
            viewBox="0 0 21 23"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M17.5493 8.73181H3.4507V20.2052H17.5493V8.73181ZM4.46948 19.1852V9.75184H16.5305V19.1852H4.46948Z"
              fill="black"
            />
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M5.32394 0C4.66902 0 4.14085 0.53697 4.14085 1.19594V1.74645H1.52817C0.682665 1.74645 0 2.4398 0 3.29168V21.4548C0 22.3066 0.682665 23 1.52817 23H19.4718C20.3173 23 21 22.3067 21 21.4548V3.29168C21 2.4398 20.3173 1.74645 19.4718 1.74645H16.8592V1.19594C16.8592 0.53697 16.331 0 15.6761 0C15.0211 0 14.493 0.53697 14.493 1.19594V1.74645H6.50704V1.19594C6.50704 0.53697 5.97887 0 5.32394 0ZM5.12676 1.19594C5.12676 1.08328 5.21656 0.994718 5.32394 0.994718C5.43133 0.994718 5.52113 1.08328 5.52113 1.19594V3.29168C5.52113 3.40434 5.43133 3.4929 5.32394 3.4929C5.21656 3.4929 5.12676 3.40434 5.12676 3.29168V1.19594ZM15.4789 1.19594C15.4789 1.08328 15.5687 0.994718 15.6761 0.994718C15.7834 0.994718 15.8732 1.08328 15.8732 1.19594V3.29168C15.8732 3.40434 15.7834 3.4929 15.6761 3.4929C15.5687 3.4929 15.4789 3.40434 15.4789 3.29168V1.19594ZM0.985916 3.29168C0.985916 2.98611 1.23021 2.74117 1.52817 2.74117H4.14085V3.29168C4.14085 3.95065 4.66902 4.48762 5.32394 4.48762C5.97887 4.48762 6.50704 3.95065 6.50704 3.29168V2.74117H14.493V3.29168C14.493 3.95065 15.0211 4.48762 15.6761 4.48762C16.331 4.48762 16.8592 3.95065 16.8592 3.29168V2.74117H19.4718C19.7698 2.74117 20.0141 2.98611 20.0141 3.29168V5.93793H0.985916V3.29168ZM0.985916 21.4548V6.93265H20.0141V21.4548C20.0141 21.7603 19.7698 22.0053 19.4718 22.0053H1.52817C1.23021 22.0053 0.985916 21.7603 0.985916 21.4548Z"
              fill="black"
            />
          </svg>
          <input
            id="check-in"
            type="text"
            title="Start Date"
            v-model="props.startDate"
            placeholder="Check In"
            :readonly="!props.isTypeable"
          />
        </label>
        <label for="check-out">
          <svg
            width="21"
            height="23"
            viewBox="0 0 21 23"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M17.5493 8.73181H3.4507V20.2052H17.5493V8.73181ZM4.46948 19.1852V9.75184H16.5305V19.1852H4.46948Z"
              fill="black"
            />
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M5.32394 0C4.66902 0 4.14085 0.53697 4.14085 1.19594V1.74645H1.52817C0.682665 1.74645 0 2.4398 0 3.29168V21.4548C0 22.3066 0.682665 23 1.52817 23H19.4718C20.3173 23 21 22.3067 21 21.4548V3.29168C21 2.4398 20.3173 1.74645 19.4718 1.74645H16.8592V1.19594C16.8592 0.53697 16.331 0 15.6761 0C15.0211 0 14.493 0.53697 14.493 1.19594V1.74645H6.50704V1.19594C6.50704 0.53697 5.97887 0 5.32394 0ZM5.12676 1.19594C5.12676 1.08328 5.21656 0.994718 5.32394 0.994718C5.43133 0.994718 5.52113 1.08328 5.52113 1.19594V3.29168C5.52113 3.40434 5.43133 3.4929 5.32394 3.4929C5.21656 3.4929 5.12676 3.40434 5.12676 3.29168V1.19594ZM15.4789 1.19594C15.4789 1.08328 15.5687 0.994718 15.6761 0.994718C15.7834 0.994718 15.8732 1.08328 15.8732 1.19594V3.29168C15.8732 3.40434 15.7834 3.4929 15.6761 3.4929C15.5687 3.4929 15.4789 3.40434 15.4789 3.29168V1.19594ZM0.985916 3.29168C0.985916 2.98611 1.23021 2.74117 1.52817 2.74117H4.14085V3.29168C4.14085 3.95065 4.66902 4.48762 5.32394 4.48762C5.97887 4.48762 6.50704 3.95065 6.50704 3.29168V2.74117H14.493V3.29168C14.493 3.95065 15.0211 4.48762 15.6761 4.48762C16.331 4.48762 16.8592 3.95065 16.8592 3.29168V2.74117H19.4718C19.7698 2.74117 20.0141 2.98611 20.0141 3.29168V5.93793H0.985916V3.29168ZM0.985916 21.4548V6.93265H20.0141V21.4548C20.0141 21.7603 19.7698 22.0053 19.4718 22.0053H1.52817C1.23021 22.0053 0.985916 21.7603 0.985916 21.4548Z"
              fill="black"
            />
          </svg>
          <input
            id="check-out"
            type="text"
            title="End Date"
            v-model="props.endDate"
            placeholder="Check Out"
            :readonly="!props.isTypeable"
          />
        </label>
      </template>
      <template v-slot:navigationArrowLeft>
        <div>←</div>
      </template>
      <template v-slot:navigationArrowRight>
        <div>→</div>
      </template>
      <template v-slot:cleaner>
        <div style="display: flex; justify-content: center;">
          <button @click="test">Cancel</button>
        </div>
      </template>
      <template v-slot:footer>
        <div class="footer">
          <a
            class="button"
            @click.prevent="$refs.demoCalendar1.showCalendar = false"
            >Apply</a
          >
          <a
            class="button is-blue"
            @click.prevent="demoCalendar1.dateRange = {}"
            >Clear</a
          >
        </div>
      </template>
    </FunctionalCalendar>

  </div>
</template>

<script>
import { FunctionalCalendar } from '../index'
/* eslint-disable */
export default {
  components: { FunctionalCalendar },
  data() {
    return {
      rangesData: {
        multipleDateRange: [{ end: '7/17/2020', start: '7/3/2020' }]
      },
      demoCalendar1: {
        dateRange: {
          start: '5/20/2020',
          end: '5/25/2020'
        }
        // selectedDate: '26/5/2020'
      },
      calendarData: {},
      disabledDates: [],
      calendarConfigs: {
        isMultipleDatePicker: true,
        dayNames: ['Mo', 'Tu', 'We', 'Th', 'Fr', 'Sa', 'Su']
      }
    }
  },
  methods: {
    test() {
      console.log(this.$refs.demoCalendar1.rangeIsSelected)
    },
    eventItemHover(event) {
      console.log(event.date, event.title)
    },
    dayClicked(item) {
      console.log('clicked:' + JSON.stringify(item))
    },
    getEventsByDate(date) {
      return this.events.filter(event => event.date === date)
    },
    get(val) {
      console.log(val)
    },
    opened() {
      console.log('open')
    },
    closed() {
      console.log('close')
    },
    changedMonth(value) {
      console.log(value)
    },
    choseDay(day) {
      console.log(day)
    },
    preYear() {
      this.$refs.calendar.ChooseDate('10/10/2020')
    },
    nextYear() {
      this.$refs.calendar.NextYear()
    },
    preMonth() {
      this.$refs.calendar.PreMonth()
    },
    nextMonth() {
      this.$refs.calendar.NextMonth()
    }
  }
}
</script>

<style lang="postcss">
$color1: rgba(38, 109, 211, 1);
$color2: rgba(52, 64, 85, 1);
$color3: rgba(136, 128, 152, 1);
$color4: rgba(207, 179, 205, 1);
$color5: rgba(223, 194, 242, 1);
$color6: rgb(208, 217, 208);

html,
body {
  background-color: #222;
  padding: 0;
  margin: 0;
}

.demo-calendar {

  & .dateRangeInputs {
    & label {
      position: relative;
      display: inline-flex;
      align-items: center;

    & svg {
        position: absolute;
        width: 16px;
        left: 5px;
      }

    & input {
        border-radius: unset;
      }
    }
  }

  & .footer {
    display: flex;
    justify-content: flex-end;
    margin: 0 5px 5px 0;

  & .button {
      background-color: #4caf50; /* Green */
      border: none;
      color: white;
      padding: 5px 27px;
      text-align: center;
      text-decoration: none;
      display: inline-block;
      font-size: 16px;

      &:hover {
        cursor: pointer;
        -moz-box-shadow: inset 0 0 10px #436562;
        -webkit-box-shadow: inset 0 0 10px #436562;
        box-shadow: inset 0 0 10px #436562;
      }

      & .is-blue {
        background-color: #008cba;
      }
    }
  }
}

.console {
  font-family: Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, monospace, serif;
  background-color: #111;
  margin-bottom: 10px;
  overflow: auto;
  width: auto;
  padding: 1em;
  max-height: 600px;
}

.vfc-multiple-input input {
  cursor: pointer;
}
.vfc-hover {
  cursor: pointer;
}
</style>
