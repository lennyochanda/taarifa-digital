<script>
	import Phone24 from 'carbon-icons-svelte/lib/Phone24'
	import Email24 from 'carbon-icons-svelte/lib/Email24'
	import LogoTwitter24 from 'carbon-icons-svelte/lib/LogoTwitter24'
		import LogoFacebook24 from 'carbon-icons-svelte/lib/LogoFacebook24'

</script>

<footer>
	<div class="contact">
		<h3>Contact Info</h3>
		<ul>
			<li>
				<Phone24 />
				<p>+254702540895</p>
			</li>
			<br>
			<li>
				<Email24 />
				<p>taarifadigital@gmail.com</p>
			</li>
			<br>
			<li>
				<LogoTwitter24 />
				<a href="https://twitter.com/">
					<p>taarifadigital</p>
				</a>
			</li>
			<br>
			<li>
				<LogoFacebook24 />
				<a href="https://facebook.com/">
					<p>taarifadigital</p>
				</a>
			</li>
		</ul>
		<div class="copyright">
			<p>&copy; | 2021 Taarifa Digital</p>
			<p>All rights reserved</p>
		</div>
	</div>
</footer>

<style>
	footer {
		position: sticky;
		top: 100vh;
		padding: 1em 1.8em;
		background: linear-gradient(rgba(25, 25, 25, 0.9), rgba(25, 25, 25, 0.9), rgba(25, 25, 25, 0.9)),url(footerBg.jpg);
		background-position: center center;
		background-repeat: no-repeat;
		background-size: cover;
		color: white;
	}
	h3 {
		font-size: 1.5rem;
		font-weight: 500;
		margin-bottom: .5em;
	}
	li {
		display: inline-flex;
		align-items: center;
		padding: .4em;
		border-bottom: .8px dotted red;
	}

	p {
		margin-left: .5em;
	}

	.copyright {
		margin: 2em auto 1em;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		font-size: .6rem;
	}

	a, p {
		color: #fff;
		letter-spacing: .1em;
		font-size: .8rem;
		font-weight: 200;
	}
</style>