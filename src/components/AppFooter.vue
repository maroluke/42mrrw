<script>
import SquircleButton from "./SquircleButton.vue";
import { RouterLink } from "vue-router";
import IconLogoMini from "./icons/IconLogoMini.vue";
import IconArrow from "./icons/IconArrow.vue";

export default {
	name: "Footer",
	components: {
		SquircleButton,
		RouterLink,
		IconLogoMini,
		IconArrow,
	},

	data() {
		return {
			navigationLinks: [],
			contactIcons: {},
		};
	},

	methods: {
		// TODO: Merge next two methods into one
		getNavigationLinks() {
			const navigation = document.querySelector(".nav ul");
			const navigationItems = navigation.querySelectorAll("a");
			const navigationLinks = [];

			navigationItems.forEach((item) => {
				const linkText = item.innerText;
				const linkHref = item.getAttribute("href");
				navigationLinks.push({ linkText, linkHref });
			});

			return navigationLinks;
		},

		getContactIcons() {
			const contact = document.querySelector("nav .contact-icons");
			const contactItems = contact.querySelectorAll("li a");
			const contactIcons = [];

			contactItems.forEach((item) => {
				contactIcons.push(item);
			});

			return contactIcons;
		},

		outputContactIcons() {
			const contact = document.querySelector("footer .contact-icons");
			this.contactIcons.forEach((item) => {
				const duplicate = item.cloneNode(true);
				contact.append(duplicate);
			});
		},
	},

	mounted() {
		this.navigationLinks = this.getNavigationLinks();
		this.contactIcons = this.getContactIcons();
		this.outputContactIcons();
	},
};
</script>

<template>
	<footer
		class="bg-black px-5 py-10 flex flex-col justify-end"
	>
		<!-- <div class="absolute w-full h-full bottom-0 left-0 z-10">
			<img
				loading="lazy"
				src="/sunrise-over-Earth_1600.jpg"
				alt="Globe from outta space"
				class="z-10 block"
			/> -->
			<!-- <div class="bg-gradient-to-r from-[rgba(0,0,0,.80)] to-transparent z-20 absolute w-full h-full top-0 left-0"></div> -->
		<!-- </div> -->

		<div class="drop-shadow-md z-20 md:flex md:gap-32">
			<div class="">
				<p class="font-medium mt-5 text-base md:mt-0">
					Gemeinsam f??r ein<br /><span
						class="text-rich-electric-blue font-medium"
						>besseres Morgen</span
					>.
				</p>

				<p class="font-medium text-base">
					Lass uns zusammen <br />handeln.
				</p>
			</div>

            <div class="flex flex-col gap-10 justify-start mt-10 md:mt-0">
                <RouterLink to="/">
                    <IconLogoMini class="fill-moon" />
                </RouterLink>

                <div class="contact-icons flex gap-8 drop-shadow"></div>
            </div>
		</div>

		<hr class="my-8 border-snow bg-snow" />

		<div class="z-20 opacity-60">
			<h4 class="font-medium text-sm mb-5">Credits</h4>

			<ul>
				<li>
					<a href="#" class="text-sm"
						>Bild #1: Lawrence Aritao, Unsplash</a
					>
				</li>
				<li>
					<a href="#" class="text-sm"
						>Bild #2: Markus Spiske, Unsplash</a
					>
				</li>
				<li>
					<a href="#" class="text-sm"
						>Bild #3: Eleonore Kemmel, Unsplash</a
					>
				</li>
				<li>
					<a href="#" class="text-sm"
						>Bild #4: Clarisse Meyer, Unsplash</a
					>
				</li>
				<li>
					<a href="#" class="text-sm"
						>Bild #5: Mykhailo Kopyt, Unsplash</a
					>
				</li>
			</ul>

			<p class="text-sm font-normal mt-10 z-20">Copyright ?? 2023</p>
		</div>
	</footer>
</template>

<style>
    footer .contact-icons a svg {
        @apply !h-4;
    }

	footer .contact-icons a {
		@apply bg-snow p-1 rounded text-black opacity-75;
	}
</style>