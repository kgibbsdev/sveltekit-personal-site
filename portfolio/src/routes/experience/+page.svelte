<script>
	import {
		Timeline,
		TimelineItem,
		TimelineSeparator,
		TimelineDot,
		TimelineConnector,
		TimelineContent,
		TimelineOppositeContent
	} from 'svelte-vertical-timeline';

	const colors = {
		first: '#7CD5E2',
		second: '#FEC048',
		third: '#DD84C1',
		forth: '#FB6958'
	};

	const items = [
		{
			startDate: new Date(2019, 4, 1),
			endDate: new Date(2020, 8, 1),
			title: 'Spud Software',
			description: 'My first software job.',
			color: colors.first,
			techUsed: ['C#', 'SQL', 'JavaScript']
		}
	];

	/**
	 * @param {Date} startDate
	 * @param {Date} endDate
	 */
	function calulateTimeInYearsWithDecimal(startDate, endDate) {
		const diff = endDate - startDate;
		const years = diff / (1000 * 60 * 60 * 24 * 365.25);
		return years.toFixed(1);
	}
</script>

<Timeline
	position="alternate"
	style={`
  border-radius: 3%;
  padding: 1rem;
  `}
>
	{#each items as item}
		<TimelineItem>
			<TimelineOppositeContent slot="opposite-content">
				<p class="oposite-content-title">
					{calulateTimeInYearsWithDecimal(item.startDate, item.endDate)} years
				</p>
			</TimelineOppositeContent>

			<TimelineSeparator>
				<TimelineDot style={`background-color: ${item.color}; border-color: #fff;`} />
				<TimelineConnector />
			</TimelineSeparator>
			<TimelineContent>
				<h3 class="content-title">{item.title}</h3>
				<p class="content-description">{item.description}</p>
			</TimelineContent>
		</TimelineItem>
	{/each}
</Timeline>

<style>
	.oposite-content-title {
		margin: 0;
		padding: 0;
	}
	.content-title {
		margin: 0;
		padding: 0;
	}

	.content-description {
		margin: 0;
		padding: 0;
		margin-top: 1rem;
		color: #d1d3dd;
		font-weight: lighter;
		padding: 0.5rem 0;
	}
</style>
