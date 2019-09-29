<template>
	<div class="texteditorline">
		<div id="text-editor-line">
			<div id="editable" v-on:keydown="onClickEnter($event)" contenteditable></div>
		</div>
	</div>
</template>

<style>
	#text-editor-line {
		display: flex;
		align-items: flex-start;
	}

	#line-number {
		font-size: .8em;
		opacity: .75;
		padding-left: 15px;
	}

	#line-number > p {
		margin: 0;
	}

	#editable {
		flex-grow: 1;
	}
</style>

<script>
	export default {
		name: 'texteditorline',
		props: ['lineNo'],
		data: () => {
			return {
				shiftDown: false,
				enterDown: false,
			};
		},
		methods: {
			onClickEnter: function(evt) {
				const startDelayTimer = () => {
					if (!(this.shiftDown || this.enterDown)) {
						const btnClickDelay = setInterval(() => {
							if (this.shiftDown && this.enterDown) {
								this.$emit('enter');
							}

							this.shiftDown = false;
							this.enterDown = false;
							clearInterval(btnClickDelay);
						}, 17);
					}
				}

				switch(evt.key) {
					case 'Enter':
						startDelayTimer();
						this.enterDown = true;
						evt.preventDefault();
						return false;
					break;
					case 'Shift':
						startDelayTimer();
						this.shiftDown = true;
					break;
				}
			},
		},
	}
</script>
