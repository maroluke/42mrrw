<script>
import { useNavigationStore } from "@/stores/navigation";
import NavigationItem from "./NavigationItem.vue";
import ContactIcons from "./ContactIcons.vue";
import { RouterLink } from "vue-router";
import LogoMiniIcon from "@components/icons/IconLogoMini.vue";

export default {
	components: {
		NavigationItem,
		ContactIcons,
		RouterLink,
		LogoMiniIcon,
	},
	setup() {
		const navigationState = useNavigationStore();
		return {
			navigationState,
		};
	},
};
</script>

<template>
	<!-- Main Navigation -->
	<Transition name="nav-toggle">
		<nav
			v-show="navigationState.navigationIsOpen"
			class="nav z-50 fixed flex justify-end w-full h-full p-2 max-w-screen-sm top-0 right-0 bg-coal bg-opacity-25 backdrop-blur-sm duration-300 sm:max-w-none"
		>
			<div class="bg-snow rounded-lg overflow-hidden z-40 shadow-2xl w-full h-full max-w-screen-xs xs:h-auto xs:self-start">
				<Transition name="logo-mini-toggle" v-show="navigationState.navigationIsOpen" @click="navigationState.navigationIsOpen = false">
					<LogoMiniIcon
						class="logo text-moon transition-opacity duration-1000 delay-200 fixed ml-4 mt-4"
					/>
				</Transition>
				<div class="flex flex-col justify-between py-12 h-full">
					<!-- Close navigation button -->
					<!-- <div
						class="close-nav flex justify-between items-center cursor-pointer z-20 w-full py-4 pl-4 pr-0"
					>
						<div
							@click="navigationState.toggleNavigation"
							class="flex justify-center items-center w-10 h-5 flex-shrink"
						>
							<span
								class="w-6 h-0.5 bg-silver rotate-45 block absolute"
							></span>
							<span
								class="w-6 h-0.5 bg-silver -rotate-45 block absolute"
							></span>
						</div>
					</div> -->

					<!-- The menu -->
					<ul
						@click="navigationState.navigationIsOpen = !navigationState.navigationIsOpen"
						class="flex gap-1 flex-col z-10 flex-grow pt-5 text-dark"
					>
						<NavigationItem :to="'/community'"
							>Wir bauen eine Community</NavigationItem
						>
						<NavigationItem :to="'/projekte'"
							>Wir f??rdern Projekte</NavigationItem
						>
						<NavigationItem :to="'/wer-wir-sind'"
							>Wer wir sind</NavigationItem
						>
						<NavigationItem :to="'/sei-dabei'"
							>Sei ein Teil davon</NavigationItem
						>
						<NavigationItem :to="'/unser-weg'"
							>Unser Weg</NavigationItem
						>
					</ul>
					
					<div class="flex flex-col">
						<ul
							@click="navigationState.navigationIsOpen = !navigationState.navigationIsOpen"
							class="secondary-nav flex flex-col px-8 pt-12 pb-2 text-base text-gray-500"
						>
							<RouterLink to="/glossar"
								class="font-light hover:text-rich-electric-blue"
								>Glossar</RouterLink
							>
							<RouterLink to="/impressum"
								class="font-light hover:text-rich-electric-blue"
								>Impressum</RouterLink
							>
						</ul>

						<ContactIcons class="px-8 bg-snow" />
					</div>
				</div>
			</div>
		</nav>
	</Transition>
</template>

<style>
.nav-toggle-enter-active,
.nav-toggle-leave-active {
	@apply opacity-100 transition-opacity;
}

.nav-toggle-enter-from,
.nav-toggle-leave-to {
	@apply opacity-0;
}

.nav-open {
	@apply overflow-hidden;
}

.logo-mini-toggle-enter-active,
.logo-mini-toggle-leave-active {
	@apply opacity-100;
}

.logo-mini-toggle-enter-from,
.logo-mini-toggle-leave-to {
	@apply opacity-0 duration-200 delay-[0ms];
}
</style>
