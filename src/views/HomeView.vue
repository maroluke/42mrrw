<script>
import TheIntro from "@components/TheIntro.vue";
import QuoteCard from "@components/QuoteCard.vue";
import ParagraphWithCards from "@components/ParagraphWithCards.vue";
import TitleParagraphItem from "@components/TitleParagraphItem.vue";
import { defineComponent } from "vue";

export default defineComponent({
	components: {
		TheIntro,
		QuoteCard,
		ParagraphWithCards,
		TitleParagraphItem,
	},
	data() {
		return {
			loading: false,
			cmsData: [],
			error: null,
		};
	},
	mounted() {
		// this.loading = true;
		// this.error = this.cmsData = null;
		// const url = `/api/notion`;
		// await fetch(url)
		// 	.then((response) => response.json())
		// 	.then((data) => {
		// 		this.cmsData =
		// 			data.results[0].properties.Content.rich_text[0].plain_text;
		// 		console.log(data.results);
		// 	})
		// 	.catch((error) => {
		// 		this.error = error.toString();
		// 		console.log(this.error);
		// 	})
		// 	.finally(() => {
		// 		this.loading = false;
		// 	});
	},
	// async mounted() {
	//     this.error = this.cmsData = null
	//     this.loading = true
	//     // use route params to build the API endpoint URL
	//     const url = '/api/notion'
	//     const response = await fetch(url).then(res => res.json())

	//     this.cmsData = response

	//     console.log(response)
	// },
});
</script>

<template>
	<main class="bg-dark">
		<TheIntro
			:filename="'globe.png'"
			:rotate="0"
			:bg-gradient="true"
			class="z-20"
		>
			<template #title>
				Lass uns gemeinsam die Welt von Morgen schaffen.
			</template>

			<template #paragraph>
				Wir unterstützen nachhaltige
				Projekte dabei zu wachsen und einen positiven Beitrag für unsere
				Zukunft zu erbringen.
			</template>
		</TheIntro>

		<section
			class="px-5 py-10 bg-snow z-30 md:py-20 md:flex md:justify-center"
		>
			<div
				class="flex flex-col items-center gap-10 justify-center md:flex-row md:max-w-screen-lg"
			>
				<TitleParagraphItem class="text-coal md:basis-2/3">
					<template #title>
						Nachhaltigkeit ist nur ein erster Schritt – wir brauchen
						regenerative Ideen!
					</template>

					<template #paragraph>
						Als Kollektiv ist
						<span class="font-bold">re:morrow</span>, mit
						begeisterten & motivierten Menschen, Teil der
						Veränderung. <br /><br />
						Weg von endlosem Streben nach Profit und unendlichem
						Wachstum, hin zu sinnvollen
						Projekten, die ihre
						<RouterLink
							class="glossar-link"
							:to="{ path: `/glossar/`, hash: `#regenerativ` }"
							>regenerative</RouterLink
						>
						Kraft entfesseln.
					</template>
				</TitleParagraphItem>

				<QuoteCard class="md:basis-1/3" />
			</div>
		</section>

		<section
			class="text-snow px-5 py-10 bg-dark z-20 flex flex-col items-center md:py-20"
		>
			<TitleParagraphItem
				:button="'Unser Weg'"
				:link="'/unser-weg'"
				class="max-w-screen-md flex flex-col gap-10 !mb-0"
			>
				<template #title>
					Wir wissen, dass wir zusammen stärker sind!
				</template>

				<template #paragraph>
					Wir leisten einen Beitrag für ein besseres Morgen – und wenn wir das gemeinsam tun, ist dieser nur noch grösser! Dafür finden wir die guten Ideen und unterstützen deren Wachstum. Jeder von uns hat Stärken, die er dafür einsetzen kann. 
					<br /><br />
					Als Individuum kann man stark sein, aber als Kollektiv, sind wir Teil der Veränderung.
				</template>
			</TitleParagraphItem>
		</section>

		<ParagraphWithCards
			class="bg-snow text-coal px-5 py-10 z-20 md:py-20"
		/>

		<section
			class="text-snow px-5 py-10 bg-dark z-20 flex flex-col items-center md:py-20"
		>
			<TitleParagraphItem
				:button="'Melde dich'"
				:contact="true"
				class="max-w-screen-md flex flex-col gap-10 !mb-0 modal-toggle"
			>
				<template #title> Wohin die Reise führt. </template>

				<template #paragraph>
					Hey, wir brauchen nichts zu verstecken. Erfahre hier, wie
					unsere Roadmap aussieht. Ein Schritt nach dem anderen. So
					entwickeln wir re:morrow, wachsen und schaffen Wachstum.
					<br /><br />
					Bist du Teil unseres nächsten Schritts und hast Bock
					mitzugestalten?
				</template>
			</TitleParagraphItem>
		</section>

		<section
			class="px-5 py-10 bg-snow text-coal z-20 flex flex-col items-center md:py-20"
		>
			<TitleParagraphItem
				:button="'Entdecken'"
				:link="'/wer-wir-sind'"
				class="max-w-screen-md flex flex-col !mb-0"
			>
				<template #title> Wer wir sind. </template>

				<template #paragraph>
					Bist du neugierig, wer und was hinter re:morrow steckt?
					Erfahre mehr über die Menschen dahinter und unseren
					Blickwinkel.
				</template>
			</TitleParagraphItem>
		</section>
	</main>
</template>
