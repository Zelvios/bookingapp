<script lang="ts">
	import '../app.css';
	import { Card, Button, Label, Input, Checkbox } from 'flowbite-svelte';
	import { signedIn } from "../store";
	import { onDestroy } from "svelte";

	let isSignedIn: boolean;

	const unsubscribe = signedIn.subscribe((value) => {
		isSignedIn = value;
	});

	onDestroy(() => {
		unsubscribe();
	});

	function handleLogin(event: Event): void {
		event.preventDefault();
		signedIn.set(true);
	}
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Booking App" />
</svelte:head>

{#if !isSignedIn}
	<section style="display: flex; align-items: center; justify-content: center; height: 50vh;">
		<Card>
			<form class="flex flex-col space-y-6" action="/" on:submit={handleLogin}>
				<h3 class="text-xl font-medium text-gray-900 dark:text-white">Sign In</h3>
				<Label class="space-y-2">
					<span>Username</span>
					<Input type="text" name="email" placeholder="username" required />
				</Label>
				<Label class="space-y-2">
					<span>Your password</span>
					<Input type="password" name="password"	 required />
				</Label>
				<div class="flex items-start">
					<Checkbox>Remember me</Checkbox>
				</div>
				<Button type="submit" class="w-full">Sign In</Button>
				<div class="text-sm font-medium text-gray-500 dark:text-gray-300">
					Please contact staff with problems on Sign In.
				</div>
			</form>
		</Card>
	</section>
{:else}
	<section style="display: flex; align-items: center; justify-content: center; height: 50vh;">
		<div class="bg-green-500 p-6 rounded-lg text-white">
			<h1 class="text-2xl font-bold">Welcome Back!</h1>
			<p class="mt-4">You are now signed in. Enjoy your stay!</p>
		</div>
	</section>
{/if}

<main class="bg-white dark:bg-gray-800">

</main>
