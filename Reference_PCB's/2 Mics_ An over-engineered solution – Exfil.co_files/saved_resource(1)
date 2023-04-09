// https://www.npmjs.com/package/autosize/v/5.0.1, with the global renamed to `textarea_autosize`.
!function(e,t){"object"==typeof exports&&"undefined"!=typeof module?module.exports=t():"function"==typeof define&&define.amd?define(t):(e||self).textarea_autosize=t()}(this,function(){var e,t,n="function"==typeof Map?new Map:(e=[],t=[],{has:function(t){return e.indexOf(t)>-1},get:function(n){return t[e.indexOf(n)]},set:function(n,o){-1===e.indexOf(n)&&(e.push(n),t.push(o))},delete:function(n){var o=e.indexOf(n);o>-1&&(e.splice(o,1),t.splice(o,1))}}),o=function(e){return new Event(e,{bubbles:!0})};try{new Event("test")}catch(e){o=function(e){var t=document.createEvent("Event");return t.initEvent(e,!0,!1),t}}function r(e){var t=n.get(e);t&&t.destroy()}function i(e){var t=n.get(e);t&&t.update()}var l=null;return"undefined"==typeof window||"function"!=typeof window.getComputedStyle?((l=function(e){return e}).destroy=function(e){return e},l.update=function(e){return e}):((l=function(e,t){return e&&Array.prototype.forEach.call(e.length?e:[e],function(e){return function(e){if(e&&e.nodeName&&"TEXTAREA"===e.nodeName&&!n.has(e)){var t,r=null,i=null,l=null,d=function(){e.clientWidth!==i&&c()},u=function(t){window.removeEventListener("resize",d,!1),e.removeEventListener("input",c,!1),e.removeEventListener("keyup",c,!1),e.removeEventListener("autosize:destroy",u,!1),e.removeEventListener("autosize:update",c,!1),Object.keys(t).forEach(function(n){e.style[n]=t[n]}),n.delete(e)}.bind(e,{height:e.style.height,resize:e.style.resize,overflowY:e.style.overflowY,overflowX:e.style.overflowX,wordWrap:e.style.wordWrap});e.addEventListener("autosize:destroy",u,!1),"onpropertychange"in e&&"oninput"in e&&e.addEventListener("keyup",c,!1),window.addEventListener("resize",d,!1),e.addEventListener("input",c,!1),e.addEventListener("autosize:update",c,!1),e.style.overflowX="hidden",e.style.wordWrap="break-word",n.set(e,{destroy:u,update:c}),"vertical"===(t=window.getComputedStyle(e,null)).resize?e.style.resize="none":"both"===t.resize&&(e.style.resize="horizontal"),r="content-box"===t.boxSizing?-(parseFloat(t.paddingTop)+parseFloat(t.paddingBottom)):parseFloat(t.borderTopWidth)+parseFloat(t.borderBottomWidth),isNaN(r)&&(r=0),c()}function a(t){var n=e.style.width;e.style.width="0px",e.style.width=n,e.style.overflowY=t}function s(){if(0!==e.scrollHeight){var t=function(e){for(var t=[];e&&e.parentNode&&e.parentNode instanceof Element;)e.parentNode.scrollTop&&t.push({node:e.parentNode,scrollTop:e.parentNode.scrollTop}),e=e.parentNode;return t}(e),n=document.documentElement&&document.documentElement.scrollTop;e.style.height="",e.style.height=e.scrollHeight+r+"px",i=e.clientWidth,t.forEach(function(e){e.node.scrollTop=e.scrollTop}),n&&(document.documentElement.scrollTop=n)}}function c(){s();var t=Math.round(parseFloat(e.style.height)),n=window.getComputedStyle(e,null),r="content-box"===n.boxSizing?Math.round(parseFloat(n.height)):e.offsetHeight;if(r<t?"hidden"===n.overflowY&&(a("scroll"),s(),r="content-box"===n.boxSizing?Math.round(parseFloat(window.getComputedStyle(e,null).height)):e.offsetHeight):"hidden"!==n.overflowY&&(a("hidden"),s(),r="content-box"===n.boxSizing?Math.round(parseFloat(window.getComputedStyle(e,null).height)):e.offsetHeight),l!==r){l=r;var i=o("autosize:resized");try{e.dispatchEvent(i)}catch(e){}}}}(e)}),e}).destroy=function(e){return e&&Array.prototype.forEach.call(e.length?e:[e],r),e},l.update=function(e){return e&&Array.prototype.forEach.call(e.length?e:[e],i),e}),l});
;
(function () {
	'use strict';

	function getPostAs() {
		const postAs = document.querySelector('#hc_post_as');
		return postAs && postAs.value;
	}

	function setPostAs(value) {
		const postAs = document.querySelector('#hc_post_as');
		if (postAs) {
			postAs.value = value;
		}
	}

	function isGuest() {
		return getPostAs() === 'guest';
	}

	function hide(el) {
		if (!el) {
			return;
		}

		el.style.display = 'none';
	}

	function show(el, forceDisplay) {
		if (!el) {
			return;
		}

		el.style.removeProperty('display');
		if (forceDisplay){
			el.style.display = forceDisplay;
		}
	}

	function applyStyles(el, styles) {
		if (!el) {
			return;
		}

		Object.keys(styles || {}).forEach(prop => (el.style[prop] = styles[prop]));
	}

	function getElementOffset(el) {
		if (!el) {
			return;
		}

		const rect = el.getBoundingClientRect();
		return {
			top: rect.top + window.pageYOffset,
			left: rect.left + window.pageXOffset,
		};
	}

	function getHeightWithMargins(el) {
		if (!el) {
			return 0;
		}

		const style = getComputedStyle(el);
		return (
			el.offsetHeight +
			(parseInt(style.marginTop, 10) || 0) +
			(parseInt(style.marginBottom, 10) || 0)
		);
	}

	function getWidthWithMargins(el) {
		if (!el) {
			return 0;
		}

		const style = getComputedStyle(el);
		return (
			el.offsetWidth +
			(parseInt(style.marginLeft, 10) || 0) +
			(parseInt(style.marginRight, 10) || 0)
		);
	}

	const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

	function animate({ el, props = {}, duration = 100, cb = () => {} } = {}) {
		if (!el) {
			return;
		}

		// Convert property names to kebab case.
		props = Object.fromEntries(
			Object.entries(props).map(([prop, val]) => [
				prop.replace(/[A-Z]/g, l => `-${l.toLowerCase()}`),
				val,
			])
		);

		const currentStyles = getComputedStyle(el);
		const transitioningProperties = Object.keys(props);
		const currentProps = Object.fromEntries(
			Object.entries(props).map(([key]) => [key, currentStyles[key]])
		);

		let willAnythingChange = false;
		Object.keys(props).forEach(key => {
			willAnythingChange = willAnythingChange || currentProps[key] !== props[key];
		});

		if (prefersReducedMotion || !willAnythingChange) {
			applyStyles(el, props);
			cb();
			return;
		}

		applyStyles(el, {
			...currentProps,
			transitionProperty: transitioningProperties.join(', '),
			transitionDuration: `${duration}ms`,
		});

		let timeout;

		// Double rAF after setting styles, for browser compatibility.
		requestAnimationFrame(() => {
			requestAnimationFrame(() => {
				applyStyles(el, props);
				const handler = e => {
					if (!e || (e.target === el && transitioningProperties.includes(e.propertyName))) {
						el.style.removeProperty('transition-property');
						el.style.removeProperty('transition-duration');
						el.removeEventListener('transitionend', handler);
						el.removeEventListener('transitioncancel', handler);
						clearTimeout(timeout);
						cb();
					}
				};
				el.addEventListener('transitionend', handler);
				el.addEventListener('transitioncancel', handler);
				timeout = setTimeout(handler, duration + 50); // Fail-safe, in case there is no transition.
			});
		});
	}

	function fadeIn({ el, duration, cb = () => {} } = {}) {
		if (!el) {
			return;
		}

		el.style.removeProperty('display');
		el.style.opacity = '0';

		animate({
			el,
			props: { opacity: '1' },
			duration,
			cb: () => {
				el.style.removeProperty('opacity');
				cb();
			},
		});
	}

	function fadeOut({ el, duration, cb = () => {} } = {}) {
		if (!el) {
			return;
		}

		el.style.removeProperty('display');
		el.style.opacity = '1';

		animate({
			el,
			props: { opacity: '0' },
			duration,
			cb: () => {
				el.style.display = 'none';
				el.style.removeProperty('opacity');
				cb();
			},
		});
	}

	function slideDown({ el, duration, cb = () => {} } = {}) {
		if (!el) {
			return;
		}

		el.style.removeProperty('display');
		const finalHeight = getComputedStyle(el).height;
		el.style.height = '0';

		animate({
			el,
			props: { height: finalHeight },
			duration,
			cb: () => {
				el.style.removeProperty('height');
				cb();
			},
		});
	}

	function slideUp({ el, duration, initialDisplay, cb = () => {} } = {}) {
		if (!el) {
			return;
		}

		if (initialDisplay !== undefined) {
			el.style.display = initialDisplay;
		} else {
			el.style.removeProperty('display');
		}

		animate({
			el,
			props: { height: 0 },
			duration,
			cb: () => {
				el.style.display = 'none';
				el.style.removeProperty('height');
				cb();
			},
		});
	}

	function createTooltip(
		anchor,
		tooltipId,
		contents,
		offset = { top: 0, left: 0 },
		rtlOffset = { top: 0, left: 0 }
	) {
		if (anchor) {
			anchor.addEventListener('mouseenter', () => {
				const pos = getElementOffset(anchor);
				let style;
				if (HighlanderComments.text_direction === 'rtl') {
					style = `top:${pos.top + rtlOffset.top}px; left:${pos.left + rtlOffset.left}px;`;
				} else {
					style = `top:${pos.top + offset.top}px; left:${pos.left + offset.left}px;`;
				}

				const popup = document.createElement('div');
				popup.id = tooltipId;
				popup.classList.add('highlander-tooltip');
				document.body.appendChild(popup);
				popup.innerHTML = contents;
				popup.style = style;
			});

			anchor.addEventListener('mouseleave', () => {
				const popup = document.querySelector(`#${tooltipId}`);
				fadeOut({
					el: popup,
					cb: () => {
						popup.remove();
						document.querySelectorAll('.highlander-tooltip').forEach(el => el.remove);
					},
				});
			});
		}
	}

	function addIframe({ classes = [], src } = {}) {
		const iframe = document.createElement('iframe');
		if (classes.length) {
			iframe.classList.add(...classes);
		}
		iframe.height = '1';
		iframe.width = '1';
		iframe.style.display = 'none';
		iframe.src = src;
		document.body.appendChild(iframe);
	}

	function getCommentList() {
		const list = document.querySelectorAll(
			'#thecomments, .thecomments, #commentlist, #comment-list, #comments-list, .commentlist, .comment-list, .comments-list, .com-list, #comments'
		);
		return list.length ? list[list.length - 1] : null;
	}

	const HighlanderComments = {
		...(window.HighlanderComments || {}),
		commentList: null,

		initialHeight: 70,

		cookies: {
			facebook: 'wpc_fbc',
			twitter: 'wpc_tc',
			wordpress: 'wpc_wpc',
		},
		popups: {
			facebook: ',height=400,width=600',
			twitter: ',height=515,width=600',
			wordpress: ',height=500,width=500',
		},
		temp_cookie_data: '',
		currentParent: false,
		currentParentId: false,
		currentParentMargins: {},
		keyCodeReturn: 13,

		resizeCallback: function () {},

		init: function () {
			document.querySelectorAll('#respond').forEach(el => el.classList.add('js'));

			HighlanderComments.commentList = getCommentList();

			if ( HighlanderComments.isJetpack && HighlanderComments.readCookie( 'wpcom_highlander_3pc_check' ) === null ) {
				document.querySelectorAll( '#comment-form-nascar' ).forEach(el => hide(el));
			}

			document
				.querySelectorAll('#comment-form-nascar a')
				.forEach(el => el.addEventListener('click', HighlanderComments.clickService));

			document
				.querySelectorAll('#postas-wordpress, #postas-facebook, #postas-twitter')
				.forEach(el => el.addEventListener('click', HighlanderComments.clickExternalTab));

			window.addEventListener('message', e => {
				if (e.origin !== 'https://public-api.wordpress.com') {
					return;
				}

				let message = e && e.data;
				if (typeof message === 'string') {
					try {
						message = JSON.parse(message);
					} catch (err) {
						return;
					}
				}
			});

			document.querySelectorAll('.comment-form-field input, textarea#comment').forEach(el => {
				if (el.value !== '') {
					HighlanderComments.hideLabels(el);
				}
			});

			document.querySelectorAll('div.comment-form-fields input').forEach(el => {
				el.addEventListener('change', () => HighlanderComments.toggleLabel(el));
				el.addEventListener('focus', () => HighlanderComments.hideLabels(el));
				el.addEventListener('blur', () => HighlanderComments.showLabels(el));
			});

			document.querySelectorAll('div.comment-form-fields label').forEach(el =>
				el.addEventListener('click', () => {
					HighlanderComments.hideLabels(
						el.parentElement && el.parentElement.querySelectorAll('.comment-form-input input')
					);
				})
			);

			document.querySelectorAll('#email').forEach(el =>
				el.addEventListener('blur', () => {
					HighlanderComments.updateAvatarWithGravatar( el.value );

					const author = document.querySelector('#author');

					if (window.Gravatar && author && !author.value) {
						Gravatar.autofill(el.value, {
							displayName: 'author',
							url: 'url', // Their first available link, or profile URL if none
						});

						const afd = Gravatar.autofill_data;
						Gravatar.autofill_data = function (hash) {
							afd.call(Gravatar, hash);
							document
								.querySelectorAll('input#url')
								.forEach(el => el.dispatchEvent(new Event('change')));
							author.dispatchEvent(new Event('change'));
							author.dispatchEvent(new MouseEvent('click'));
						};
					}
				})
			);

			const textArea = document.querySelector('textarea#comment');

			if (!textArea) {
				return;
			}

			if (window.textarea_autosize) {
				textArea.addEventListener('autosize:resized', HighlanderComments.resizeCallback);
				window.textarea_autosize(textArea);
			}

			textArea.style.resize = 'none';
			textArea.dispatchEvent(new Event('change'));

			textArea.addEventListener('focus', () => HighlanderComments.hideLabels(textArea));
			textArea.addEventListener('blur', () => HighlanderComments.showLabels(textArea));

			textArea.addEventListener('keydown', e => {
				if (e.code === 'Tab') {
					e.preventDefault();

					let focusSel = '#comment-submit';
					if (isGuest()) {
						focusSel =
							HighlanderComments.comment_registration === '1' ? '#postas-wordpress' : '#email';
					}
					document.querySelectorAll(focusSel).forEach(el => el.focus());
				}

				if (HighlanderComments.isCommandOrControlKeyDown(e) && e.code === 'Enter') {
					document
						.querySelectorAll('#comment-submit')
						.forEach(el => el.dispatchEvent(new MouseEvent('click')));
				}
			});

			// Client-side form validation
			const form = document.querySelector('#commentform');
			form.addEventListener('submit', e => {
				let verified = true;
				// Comment text required
				if (textArea.value === '') {
					document.querySelectorAll('label[for="comment"]').forEach(el => {
						fadeOut({
							el,
							cb: () => {
								el.textContent = HighlanderComments.enterACommentError;
								fadeIn({
									el,
									cb: () => {
										el.classList.add('error');
									},
								});
							},
						});
					});

					document.querySelectorAll('#comment-form-comment').forEach(el => {
						el.classList.add('error');
						textArea.addEventListener('focus', () => el.classList.remove('error'), {
							once: true,
						});
					});
					verified = false;
				}

				// Only exists if email/name are required
				if (
					isGuest() &&
					(document.querySelector('#comment-form-guest label span[class="required"]') ||
						document.querySelector('#comment-form-guest label[class="error"]'))
				) {
					function handleMissingField(name, error) {
						document.querySelectorAll(`label[for="${name}"]`).forEach(el => {
							fadeOut({
								el,
								cb: () => {
									el.innerHTML = error;
									fadeIn({ el, cb: () => el.classList.add('error') });
								},
							});
						});
						document
							.querySelectorAll(`div.comment-form-${name} .comment-form-input`)
							.forEach(el => el.classList.add('error'));
						document
							.querySelectorAll(`input#${name}`)
							.forEach(el =>
								el.addEventListener(
									'focus',
									() => el.parentElement && el.parentElement.classList.remove('error'),
									{ once: true }
								)
							);

						verified = false;
					}

					const email = document.querySelector('#email') && document.querySelector('#email').value;
					if (email === '' || !email.match(/^.*@.*\..*$/)) {
						let error;
						if (email === '') {
							error = HighlanderComments.enterEmailError;
						} else {
							error = '<span class="nopublish">' + HighlanderComments.invalidEmailError + '</span>';
						}
						handleMissingField('email', error);
					}

					const author =
						document.querySelector('#author') && document.querySelector('#author').value;
					if (author === '') {
						const error = HighlanderComments.enterAuthorError;
						handleMissingField('author', error);
					}
				}

				// Don't allow "guest" comments if auth is required
				if (HighlanderComments.comment_registration === '1' && isGuest()) {
					document.querySelectorAll('#comment-form-nascar > p').forEach(el => {
						el.classList.add('error');
						fadeOut({ el, cb: () => fadeIn(el) });
					});
					verified = false;
				}

				// Set a cookie to remember which was the last used tab
				HighlanderComments.writeCookie('hc_post_as', getPostAs(), 7, '.wordpress.com');

				if (!verified) {
					e.preventDefault();
					return;
				}

				HighlanderComments.clickSubmit();
			});

			// Set up the identity block based on WP options, logged in state, etc
			if (HighlanderComments.comment_registration === '1') {
				// Must be logged in to comment (guest commenting not allowed)
				document.querySelectorAll('#comment-form-guest').forEach(el => hide(el));
				if (!HighlanderComments.isJetpack && !HighlanderComments.userIsLoggedIn) {
					// Force to guest posting if they're not logged in, which should actually not allow itself
					HighlanderComments.clickGuestTab();
					document
						.querySelectorAll('#comment-form-wordpress')
						.forEach(el => el.classList.remove('selected'));
					setPostAs('guest');
				}
			} else {
				// Guest commenting is allowed
				if (
					HighlanderComments.userIsLoggedIn &&
					document.querySelector('#comment-form-wordpress.selected')
				) {
					// User is logged in and we're looking at the WP UI already, get rid of guest commenting
					hide(document.querySelector('#comment-form-guest'));
				}
			}
			const selected = document.querySelector('.comment-form-service.selected');
			if (selected && !selected.matches('#comment-form-guest')) {
				// Something other than Guest is selected, hide the auth strip
				hide(document.querySelector('#comment-form-nascar'));
			}

			if (typeof addComment !== 'undefined') {
				HighlanderComments._moveForm = addComment.moveForm;
				addComment.moveForm = HighlanderComments.moveForm;
			}

			// Hover Tooltips
			createTooltip(
				document.querySelector('#comment-form-guest .comment-form-avatar'),
				'hltt-grav',
				HighlanderComments.gravatarFromEmail,
				{ top: -10, left: 35 },
				{ top: -10, left: -130 }
			);

			createTooltip(
				document.querySelector('#comment-form-nascar ul'),
				'hltt-auth',
				HighlanderComments.logInToExternalAccount,
				{ top: -12, left: -125 },
				{ top: -12, left: 125 }
			);
		},

		isCommandOrControlKeyDown: function (event) {
			// event.metaKey will be true if Command key (⌘) or Windows key is down.
			return event.ctrlKey || event.metaKey;
		},

		_moveForm: null,
		moveForm: function (commId, parentId, respondId, postId) {
			if (HighlanderComments._moveForm === null) {
				return;
			}

			const respond = document.querySelector(`#${respondId}`);
			if (!respond) {
				return;
			}

			respond.style.marginLeft = 0;
			respond.style.marginRight = 0;

			const t = this;

			let r = false;
			let rHeight;

			if (HighlanderComments.currentParent) {
				if (parentId === HighlanderComments.currentParentId) {
					return false;
				}

				const wTop = window.scrollY;
				const commElOffset = getElementOffset(document.querySelector(`#${commId}`));
				const cTop = commElOffset && commElOffset.top;
				const rTop = getElementOffset(respond).top;

				if (rTop <= cTop) {
					rHeight = getHeightWithMargins(respond);
					const placeholder = document.createElement('div');
					placeholder.id = 'highlander-placeholder';
					applyStyles(placeholder, {
						margin: 0,
						padding: 0,
						border: 0,
						height: `${rHeight}px`,
						visibility: 'hidden',
						position: getComputedStyle(respond).position,
					});
					respond.before(placeholder);
				}

				r = HighlanderComments._moveForm.call(t, commId, parentId, respondId, postId);
				if (r !== false) {
					return r;
				}

				applyStyles(HighlanderComments.currentParent, HighlanderComments.currentParentMargins);

				document.querySelectorAll('#highlander-placeholder').forEach(el => el.remove());

				if (rTop <= cTop) {
					try {
						window.scrollTo({ left: window.scrollX, top: wTop - rHeight, behavior: 'smooth' });
					} catch (err) {
						window.scrollTo(window.scrollX, wTop - rHeight);
					}
				}

				HighlanderComments.moveFormNow.call(t, commId, parentId, respondId);
			} else {
				r = HighlanderComments._moveForm.call(t, commId, parentId, respondId, postId);
				if (r === false) {
					HighlanderComments.moveFormNow.call(t, commId, parentId, respondId);
				}
			}

			return r;
		},

		moveFormNow: function (commId, parentId, respondId) {
			const comment = document.querySelector(`#comment-${parentId}`);
			let currentParent = comment && comment.closest('.highlander-comment');

			if (!currentParent) {
				currentParent = comment && comment.closest('.comment');
			}
			HighlanderComments.currentParentId = parentId;

			const respond = document.querySelector(`#${respondId}`);

			if (!currentParent || !respond) {
				return;
			}

			if (!currentParent.querySelector(`#${respondId}`)) {
				const el = currentParent.parentElement;
				let betterParent = el.closest('.children');
				if (!betterParent) {
					betterParent = el.closest('.highlander-comment');
					if (!betterParent) {
						betterParent = el.closest('.comment');
					}
				}

				if (betterParent) {
					currentParent = betterParent;
				}
			}

			const style = getComputedStyle(currentParent);
			const currentParentMargins = {
				backgroundColor: style.backgroundColor,
				marginLeft: style.marginLeft,
				marginRight: style.marginRight,
			};

			// Register the new values.
			HighlanderComments.currentParent = currentParent;
			HighlanderComments.currentParentMargins = currentParentMargins;

			let autoWidth = false;

			const offOrder =
				HighlanderComments.text_direction === 'rtl' ? ['Left', 'Right'] : ['Right', 'Left'];

			const parentOffset = getElementOffset(currentParent);

			offOrder.forEach(v => {
				const outerWidth = getWidthWithMargins(currentParent);

				if (currentParentMargins[`margin${v}`] === '0px') {
					const oldOff = parentOffset.left + v === 'Right' ? outerWidth : 0;
					currentParent.style[`margin${v}`] = '0px';
					let newOff = parentOffset.left + v === 'Right' ? outerWidth : 0;
					if (oldOff !== newOff) {
						newOff = v === 'Right' ? newOff - oldOff : oldOff - newOff;
						currentParent.style[`margin${v}`] = newOff;
						currentParentMargins[`margin${v}`] = newOff;
						autoWidth = true;
					}
				}
			});

			if (autoWidth) {
				currentParent.width = 'auto';
				currentParentMargins.width = 'auto';
			}

			const rgbaTransparent = /rgba.*,\s*0\s*\)/;

			if (
				currentParentMargins.backgroundColor === 'transparent' ||
				currentParentMargins.backgroundColor.match(rgbaTransparent)
			) {
				let el = currentParent;
				let bg = 'transparent';
				let bgi = getComputedStyle(el).backgroundImage;

				while (
					bgi === 'none' &&
					el.parentNode &&
					el.parentNode !== document &&
					(bg === 'transparent' || bg.match(rgbaTransparent))
				) {
					el = el.parentNode;
					bgi = getComputedStyle(el).backgroundImage;
					bg = getComputedStyle(el).backgroundColor;
				}

				currentParent.style.backgroundColor = bg;
			}

			const cancel = document.getElementById('cancel-comment-reply-link');
			let listOffsetSource = HighlanderComments.commentList;

			let redoMargins = false;
			let grandWidth;

			// Re-initialize the commentList if it was not found during init
			if (!listOffsetSource) {
				listOffsetSource = HighlanderComments.commentList = getCommentList();
			}

			let cp = HighlanderComments.currentParent;
			while (cp !== HighlanderComments.commentList && cp !== document) {
				const style = getComputedStyle(cp);
				if (style.overflow === 'hidden' || style.overflowX === 'hidden') {
					listOffsetSource = cp;
					break;
				}

				cp = cp.parentElement;
			}

			const listOffset = getElementOffset(listOffsetSource);

			HighlanderComments._unmoveForm = cancel.onclick;
			cancel.onclick = function () {
				return HighlanderComments.unmoveForm.call(this);
			};

			if (currentParentMargins.marginLeft.toString().includes('%')) {
				grandWidth = currentParent.parentElement.offsetWidth;
				currentParentMargins.marginLeft =
					(parseFloat(currentParentMargins.marginLeft) / 100) * grandWidth;
				redoMargins = true;
			}

			if (currentParentMargins.marginRight.toString().includes('%')) {
				grandWidth = currentParent.parentElement.offsetWidth;
				currentParentMargins.marginRight =
					(parseFloat(currentParentMargins.marginRight) / 100) * grandWidth;
				redoMargins = true;
			}

			if (redoMargins) {
				applyStyles(currentParent, currentParentMargins);
			}

			const currentMargins = {
				left: parseInt(getComputedStyle(currentParent).marginLeft, 10),
				right: parseInt(getComputedStyle(currentParent).marginRight, 10),
			};

			listOffset.right = listOffset.left + getWidthWithMargins(listOffsetSource);
			parentOffset.left -= currentMargins.left;
			parentOffset.right = parentOffset.left + getWidthWithMargins(currentParent);

			hide(respond);
			animate({
				el: currentParent,
				props: {
					marginLeft: `${currentMargins.left - (parentOffset.left - listOffset.left)}px`,
					marginRight: `${currentMargins.right - (listOffset.right - parentOffset.right)}px`,
				},
				duration: 300,
				cb: () => {
					slideDown({
						el: respond,
						duration: 300,
						cb: () => {
							document.querySelectorAll(`#${commId} .comment-reply-link`).forEach(el => el.focus());
							document.querySelectorAll('#comment').forEach(el => el.focus());
							HighlanderComments.resizeCallback();

							const clearDiv = document.createElement('div');
							clearDiv.classList.add('clear');
							clearDiv.id = 'threaded-clear';
							respond.querySelector('form').after(clearDiv);
						},
					});
				},
			});
		},

		_unmoveForm: null,
		unmoveForm: function () {
			const r = HighlanderComments._unmoveForm.call(this);
			if (r !== false) {
				return r;
			}

			animate({
				el: HighlanderComments.currentParent,
				props: HighlanderComments.currentParentMargins,
				duration: 300,
				cb: () => {
					applyStyles(HighlanderComments.currentParent, HighlanderComments.currentParentMargins);
					HighlanderComments.currentParent = false;
					HighlanderComments.currentParentId = false;
				},
			});

			show(document.querySelector('#respond'));
			document.querySelectorAll('#respond div#threaded-clear').forEach(el => el.remove());
			HighlanderComments.resizeCallback();

			return r;
		},

		// Escape an input string.
		HTMLToText: function (string) {
			const temp = document.createElement('span');
			temp.textContent = string;
			return `${temp.innerHTML}`;
		},

		switchAccount: function () {
			document.querySelectorAll('.comment-form-service').forEach(el => {
				el.classList.remove('selected');
				hide(el);
			});

			setPostAs('guest');
			document
				.querySelectorAll('#comment-form-nascar > p')
				.forEach(el => el.classList.remove('error'));
			show(document.querySelector('#comment-form-nascar'));

			if (HighlanderComments.comment_registration === '1') {
				hide(document.querySelector('#comment-form-guest')); // Guest commenting not allowed
				HighlanderComments.resizeCallback();
			} else {
				slideDown({
					el: document.querySelector('#comment-form-guest'),
					cb: HighlanderComments.resizeCallback,
				});
				HighlanderComments.clickGuestTab();
			}
		},

		setConnectingToText: function (serviceFriendlyName) {
			document
				.querySelectorAll('#comment-form-load-service p')
				.forEach(
					el =>
						(el.textContent = HighlanderComments.connectingToText.replace(
							'%s',
							serviceFriendlyName
						))
				);
		},

		updateLoadServiceVisibility: function (tab) {
			document.querySelectorAll('.comment-form-service').forEach(el => {
				el.style.visibility = 'visible';
				el.classList.remove('selected');

				if (el.matches(tab)) {
					show(el, 'block');
				} else {
					hide(el);
				}
			});
		},

		clickService: function (e) {
			e.preventDefault();

			const tab = this.href.replace(/^.*#/, '#').split(':');

			if (tab[0] === '#comment-form-load-service' && tab[1]) {
				HighlanderComments.setConnectingToText(tab[1]);
			} else {
				setPostAs(tab[0].split('-').pop());
			}

			HighlanderComments.updateLoadServiceVisibility('#comment-form-load-service');

			document
				.querySelectorAll('#comment-form-nascar li.selected')
				.forEach(el => el.classList.remove('selected'));
			e.target.closest('li').classList.add('selected');
			HighlanderComments.resizeCallback();
		},

		setServiceSelected: function (service) {
			HighlanderComments.updateLoadServiceVisibility('#comment-form-load-service');
			document
				.querySelectorAll('#comment-form-nascar li.selected')
				.forEach(el => el.classList.remove('selected'));
			document.querySelectorAll(`#postas-${service}`).forEach(el => el.parentElement.classList.add('selected'));
			hide(document.querySelector('#comment-form-nascar'));
			HighlanderComments.resizeCallback();
		},

		clickGuestTab: function (e) {
			const guest = document.querySelector('#comment-form-guest');

			if (HighlanderComments.comment_registration === '1') {
				hide(guest);
			} else {
				guest.classList.add('selected');
			}

			const email = document.querySelector('#email');
			if (email && email.value.includes('@twitter.example.com')) {
				email.value = '';
				email.blur();
			}

			HighlanderComments.updateAvatarWithGravatar( email && email.value );

			// Reenable subscription options
			document.querySelectorAll('#comment-form-subscribe').forEach(el => {
				el.style.opacity = 1;
				el.querySelectorAll('input').forEach(input => input.removeAttribute('disabled'));
			});
			HighlanderComments.resizeCallback();
		},

		updateAvatarWithGravatar: function ( emailValue ) {
			const gravBase =
				('https:' === location.protocol ? 'https://secure' : 'http://www') +
				'.gravatar.com/avatar/';

			// When Avatars are disabled, Gravatar can be undefined, so we check against that first
			// and fall back to an unknown gravatar if it isn't
			let gravSource = gravBase + 'ad516503a11cd5ca435acc9bb6523536?s=54&forcedefault=1';

			if ( typeof Gravatar !== 'undefined' && emailValue ) {
				gravSource = gravBase + Gravatar.md5( emailValue.toLowerCase().trim() ) + '?s=25';
			}

			if (HighlanderComments.gravDefault !== 'gravatar_default') {
				gravSource += '&d=' + encodeURIComponent(HighlanderComments.gravDefault);
			}

			document
				.querySelectorAll('#comment-form-guest .comment-form-avatar img')
				.forEach(el => el.setAttribute('src', gravSource));
		},

		getServiceData: function (service) {
			const data = HighlanderComments.readCookie(HighlanderComments.cookies[service]);

			if (data === null || typeof data.access_token === 'undefined' || !data.access_token) {
				return false;
			}
			return data;
		},

		ext_win: false,
		ext_win_check: false,
		pollExternalWindow: function (service, from_tab) {
			if (!HighlanderComments.ext_win || HighlanderComments.ext_win.closed) {
				// If the cookie is available, then we must have auth'd successfully
				const foo = HighlanderComments.getServiceData(service);
				if (HighlanderComments.getServiceData(service)) {
					HighlanderComments.doExternalLoggedIn(service);
					return;
				}
				HighlanderComments.doExternalCanceled(service, from_tab);
				HighlanderComments.ext_win = false;
				clearInterval(HighlanderComments.ext_win_check);
			}
		},

		cancelExternalWindow: function () {
			if (HighlanderComments.ext_win) {
				HighlanderComments.ext_win.close();
			}
			HighlanderComments.doExternalCanceled(getPostAs(), true);
		},

		clickExternalTab: function (e) {
			if (typeof e === 'undefined') {
				return;
			}

			let fromTab = 1;
			let service;
			if (typeof e === 'string') {
				service = e;
			} else {
				service = e.currentTarget.id.split('-')[1];
				if (!e.currentTarget.matches('a')) {
					fromTab = 0;
				}
			}

			slideUp({
				el: document.querySelector('#comment-form-guest'),
				initialDisplay: 'block',
				cb: () => {
					hide(document.querySelector('#comment-form-nascar'));

					HighlanderComments.resizeCallback();

					clearInterval(HighlanderComments.ext_win_check);
					document.querySelectorAll('.highlander-tooltip').forEach(el => el.remove());

					if (
						// Found commenting cookies
						HighlanderComments.readCookie(HighlanderComments.cookies[service]) !== null &&
						// WordPress tab, and we're logged in
						((service === 'wordpress' && HighlanderComments.userIsLoggedIn) ||
							// Not WordPress tab
							service !== 'wordpress')
					) {
						if (fromTab) {
							HighlanderComments.doExternalLoggedIn(service);
						}
					} else {
						HighlanderComments.ext_win = window.open(
							`${HighlanderComments.connectURL}&service=${service}`,
							'highconn',
							`status=0,toolbar=0,location=1,menubar=0,directories=0,resizable=1,scrollbars=0${HighlanderComments.popups[service]}`
						);
						HighlanderComments.ext_win_check = setInterval(
							() => HighlanderComments.pollExternalWindow(service, fromTab),
							100
						);
					}
				},
			});
		},

		doExternalLoggedIn: function (service) {
			clearInterval(HighlanderComments.ext_win_check);

			const data = HighlanderComments.getServiceData(service);

			if (typeof data !== 'object') {
				return;
			}

			if (service === 'wordpress') {
				// Allow subscription options
				document.querySelectorAll('#comment-form-subscribe').forEach(el => {
					el.style.opacity = '1';
					el.querySelectorAll('input').forEach(input => input.removeAttribute('disabled'));
				});

				// Set up Gravatar and flag as logged in. Load a page to trigger cookies etc
				document
					.querySelectorAll(`#comment-form-${service} .comment-form-avatar img`)
					.forEach(el => el.setAttribute('src', data.avatar));
				HighlanderComments.userIsLoggedIn = true;
				if (!HighlanderComments.isJetpack) {
					addIframe({
						src: `${HighlanderComments.homeURL}highlander.login/`,
						classes: ['highlander-auth-init'],
					});
				}
			} else if (service === 'facebook') {
				document
					.querySelectorAll(`#comment-form-${service} .comment-form-avatar img`)
					.forEach(el => el.setAttribute('src', data.avatar));
			} else {
				if (service === 'twitter') {
					// Disable subscription options for Twitter since we don't have an email
					document.querySelectorAll('#comment-form-subscribe').forEach(el => {
						el.style.opacity = '0.5';
						el.querySelectorAll('input').forEach(input => {
							input.disabled = true;
							input.removeAttribute('checked');
						});
					});
				}

				// Run all external avatars through ImgPress to resize them
				let url = data.avatar;
				try {
					if (data.avatar.match(/^(https?:)?\/\/i[012]\.wp\.com\//)) {
						url = data.avatar.replace(/^https?:/, location.protocol);
					} else if (data.avatar.match(/^(https?:)?\/\/(.*?\.)gravatar\.com\//)) {
						url = data.avatar.replace(/^https?:/, location.protocol);
					} else {
						const avatarURL = new URL(data.avatar, location);

						url = `${location.protocol}//i0.wp.com/${avatarURL.host}${avatarURL.pathname}?`;
						if (host === 'graph.facebook.com' && query.length) {
							url += 'q=' + encodeURIComponent(query) + '&';
						}
						url += 'resize=25%2C25';
					}
				} catch (error) {
					url = data.avatar;
				}

				document
					.querySelectorAll(`#comment-form-${service} .comment-form-avatar img`)
					.forEach(el => el.setAttribute('src', url));
			}

			document.querySelectorAll('#email').forEach(el => {
				el.value = data.email;
				el.dispatchEvent(new Event('change'));
			});
			document.querySelectorAll('#author').forEach(el => {
				el.value = data.name;
				el.dispatchEvent(new Event('change'));
			});
			document.querySelectorAll('#url').forEach(el => {
				el.value = data.link;
				el.dispatchEvent(new Event('change'));
				el.dispatchEvent(new MouseEvent('click'));
			});
			document.querySelectorAll(`#${service}-avatar`).forEach(el => (el.value = data.avatar));
			document.querySelectorAll(`#${service}-user_id`).forEach(el => (el.value = data.uid));
			document
				.querySelectorAll(`#${service}-access_token`)
				.forEach(el => (el.value = data.access_token));

			setPostAs(service);

			// The child of the li.selected can be a <A> (WP, FB, Twitter) or an <IFRAME> (Google)
			const selectedLink = document.querySelector('#comment-form-nascar li.selected a');
			const selectedIFrame = document.querySelector('#comment-form-nascar li.selected iframe');

			if (
				(selectedLink && service === selectedLink.id.replace('postas-', ''))
			) {
				hide(document.querySelector('#comment-form-load-service'));
				show(document.querySelector(`#comment-form-${service}`), 'block');
				document
					.querySelectorAll(`#comment-form-${service} .comment-form-posting-as strong`)
					.forEach(el => (el.textContent = data.name + ':'));
				HighlanderComments.resizeCallback();
			}
		},

		doExternalCanceled: function (service, from_tab) {
			if (from_tab) {
				let gravSource = `${
					location.protocol === 'https:' ? 'https://secure' : 'http://www'
				}.gravatar.com/avatar/ad516503a11cd5ca435acc9bb6523536?s=25`;
				if (HighlanderComments.gravDefault !== 'gravatar_default') {
					gravSource += '&d=' + encodeURIComponent(HighlanderComments.gravDefault);
				}
				document
					.querySelectorAll(`#comment-form-${service} .comment-form-avatar img`)
					.forEach(el => el.setAttribute('src', gravSource));
				document.querySelectorAll(`.comment-meta-${service}`).forEach(el => (el.value = ''));
				document
					.querySelectorAll(`#postas-${service} span`)
					.forEach(el => (el.innerHTML = '&nbsp; &nbsp; &nbsp;'));
				hide(document.querySelector(`#comment-form-${service}`));
				HighlanderComments.switchAccount();
			}
		},

		doExternalLogout: function (service) {
			let hostname;
			if (document.location.hostname.includes('.wordpress.com')) {
				hostname = 'wordpress.com';
			} else {
				hostname = document.location.hostname;
			}

			HighlanderComments.writeCookie(HighlanderComments.cookies[service], '', -10, hostname);
			HighlanderComments.doExternalCanceled(service, true);

			if (service === 'wordpress') {
				HighlanderComments.userIsLoggedIn = false;
				addIframe({ src: HighlanderComments.logoutURL });
			}
		},

		clickSubmit: function (e) {
			document.querySelectorAll('#respond input#comment-submit').forEach(el => {
				el.value = HighlanderComments.HTMLToText(HighlanderComments.submittingText);
				el.classList.add('disabled');
				el.disabled = true;
				const p = document.createElement('p');
				p.id = 'comment-form-submitting';
				el.before(p);
				el.remove();
				p.appendChild(el);
			});
		},

		toggleLabel: function (inputs) {
			if (window.innerWidth && window.innerWidth <= 450) {
				return;
			}

			inputs = inputs instanceof Node ? [inputs] : inputs;
			inputs.forEach(input => {
				const parent = input.closest('div.comment-form-field');
				if (parent) {
					parent
						.querySelectorAll('label')
						.forEach(label => (label.style.opacity = input.value.length ? 0.05 : 1));
				}
			});
		},

		hideLabels: function (inputs) {
			inputs = inputs instanceof Node ? [inputs] : inputs;
			inputs.forEach(input => {
				if (window.innerWidth === 0 || (window.innerWidth > 450 && !input.placeholder)) {
					const parent = input.closest('div.comment-form-field');
					if (parent) {
						if (!input.value.length) {
							parent.querySelectorAll('label').forEach(label => fadeOut({ el: label }));
						} else {
							parent.querySelectorAll('label').forEach(label => hide(label));
						}
					}
				}

				input.parentElement.classList.add('active');
			});
		},

		showLabels: function (inputs) {
			inputs = inputs instanceof Node ? [inputs] : inputs;
			inputs.forEach(input => {
				if (window.innerWidth === 0 || (window.innerWidth > 450 && !input.placeholder)) {
					const parent = input.closest('div.comment-form-field');
					if (parent) {
						if (!input.value.length) {
							parent.querySelectorAll('label').forEach(label => fadeIn({ el: label }));
						} else {
							parent.querySelectorAll('label').forEach(label => show(label));
						}
					}
				}

				input.parentElement.classList.remove('active');
			});
		},

		/* Read the contents of a named cookie, assuming they are query-string-style
    delimited, and return them as a JS hash. */
		readCookie: function (c) {
			const nameEQ = c + '=';
			let cookieStrings = document.cookie.split(';');

			for (let i = 0; i < cookieStrings.length; i++) {
				let cookieString = cookieStrings[i];
				while (cookieString.charAt(0) === ' ') {
					cookieString = cookieString.substring(1, cookieString.length);
				}
				if (cookieString.indexOf(nameEQ) === 0) {
					const chunk = cookieString.substring(nameEQ.length, cookieString.length);
					const pairs = chunk.split('&');
					let cookie_data = {};
					for (let num = pairs.length - 1; num >= 0; num--) {
						const pair = pairs[num].split('=');
						cookie_data[pair[0]] = decodeURIComponent(pair[1]);
					}
					return cookie_data;
				}
			}
			return null;
		},

		writeCookie: function (name, value, days, domain) {
			let expires;
			if (days) {
				const date = new Date();
				date.setTime(date.getTime() + days * 24 * 60 * 60 * 1000);
				expires = '; expires=' + date.toGMTString();
			} else {
				expires = '';
			}

			if (domain) {
				domain = '; domain=' + domain;
			} else {
				domain = '';
			}

			HighlanderComments.temp_cookie_data = document.cookie =
				name + '=' + value + expires + '; path=/' + domain;
		},
	};

	window.HighlanderComments = HighlanderComments;

	if (document.readyState !== 'loading') {
		HighlanderComments.init();
	} else {
		document.addEventListener('DOMContentLoaded', HighlanderComments.init);
	}
})();
;
