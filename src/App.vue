<script>
	import FullCalendar from '@fullcalendar/vue3'
	import dayGridPlugin from '@fullcalendar/daygrid'
	import timeGridPlugin from '@fullcalendar/timegrid'
	import interactionPlugin from '@fullcalendar/interaction'

	export default {
		components: {
			FullCalendar
		},
		data() {
			return {
				calendarOptions: {
					plugins: [dayGridPlugin, timeGridPlugin, interactionPlugin],
					initialView: 'dayGridMonth',
					dateClick: this.handleDateClick,
					events: [
						{ title: 'event 1', date: '2019-04-01' },
						{ title: 'event 2', date: '2019-04-02' }
					],
					weekends: true,
					headerToolbar: {
						left: 'title',
						center: 'dayGridMonth, timeGridWeek, timeGridDay',
						right: 'prev,next'
					}
				}
			}
		},
		methods: {
			handleDateClick: function (arg) {
				alert('date click! ' + arg.dateStr)
			},
			toggleWeekends: function () {
				this.calendarOptions.weekends = !this.calendarOptions.weekends
			}
		}
	}
</script>

<template>
	<button @click="toggleWeekends">Toggle weekends</button>
	<FullCalendar :options="calendarOptions" />
</template>

<style scoped>
</style>
