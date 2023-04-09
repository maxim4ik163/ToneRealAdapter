( function ( g ) {

  var t = {
      PLATFORM_WINDOWS: 'windows',
      PLATFORM_IPHONE: 'iphone',
      PLATFORM_IPOD: 'ipod',
      PLATFORM_IPAD: 'ipad',
      PLATFORM_BLACKBERRY: 'blackberry',
      PLATFORM_BLACKBERRY_10: 'blackberry_10',
      PLATFORM_SYMBIAN: 'symbian_series60',
      PLATFORM_SYMBIAN_S40: 'symbian_series40',
      PLATFORM_J2ME_MIDP: 'j2me_midp',
      PLATFORM_ANDROID: 'android',
      PLATFORM_ANDROID_TABLET: 'android_tablet',
      PLATFORM_FIREFOX_OS: 'firefoxOS',
      PLATFORM_MOBILE_GENERIC: 'mobile_generic',

      userAgent : false, // Shortcut to the browser User Agent String.
      matchedPlatformName : false, // Matched platform name. False otherwise.
      matchedUserAgentName : false, // Matched UA String. False otherwise.

      init: function() {
        try {
          t.userAgent = g.navigator.userAgent.toLowerCase();
          t.getPlatformName();
          t.getMobileUserAgentName();
        }	catch ( e ) {
          console.error( e );
        }
      },

      initForTest: function( userAgent ) {
        t.matchedPlatformName = false;
        t.matchedUserAgentName = false;
        try {
          t.userAgent = userAgent.toLowerCase();
          t.getPlatformName();
          t.getMobileUserAgentName();
        }	catch ( e ) {
          console.error( e );
        }
      },

      /**
       * This method detects the mobile User Agent name.
       */
      getMobileUserAgentName: function() {
        if ( t.matchedUserAgentName !== false )
          return t.matchedUserAgentName;

        if ( t.userAgent === false )
          return false;

        if ( t.isChromeForIOS() )
          t.matchedUserAgentName = 'chrome-for-ios';
        else if ( t.isTwitterForIpad() )
          t.matchedUserAgentName =  'twitter-for-ipad';
        else if ( t.isTwitterForIphone() )
          t.matchedUserAgentName =  'twitter-for-iphone';
        else if ( t.isIPhoneOrIPod() )
          t.matchedUserAgentName = 'iphone';
        else if ( t.isIPad() )
          t.matchedUserAgentName = 'ipad';
        else if ( t.isAndroidTablet() )
          t.matchedUserAgentName = 'android_tablet';
        else if ( t.isAndroid() )
          t.matchedUserAgentName = 'android';
        else if ( t.isBlackberry10() )
          t.matchedUserAgentName = 'blackberry_10';
        else if ( has( 'blackberry' ) )
          t.matchedUserAgentName = 'blackberry';
        else if ( t.isBlackberryTablet() )
          t.matchedUserAgentName = 'blackberry_tablet';
        else if ( t.isWindowsPhone7() )
          t.matchedUserAgentName = 'win7';
        else if ( t.isWindowsPhone8() )
          t.matchedUserAgentName = 'winphone8';
        else if ( t.isOperaMini() )
          t.matchedUserAgentName = 'opera-mini';
        else if ( t.isOperaMobile() )
          t.matchedUserAgentName = 'opera-mobi';
        else if ( t.isKindleFire() )
          t.matchedUserAgentName = 'kindle-fire';
        else if ( t.isSymbianPlatform() )
          t.matchedUserAgentName = 'series60';
        else if ( t.isFirefoxMobile() )
          t.matchedUserAgentName = 'firefox_mobile';
        else if ( t.isFirefoxOS() )
          t.matchedUserAgentName = 'firefoxOS';
        else if ( t.isFacebookForIphone() )
          t.matchedUserAgentName = 'facebook-for-iphone';
        else if ( t.isFacebookForIpad() )
          t.matchedUserAgentName = 'facebook-for-ipad';
        else if ( t.isWordPressForIos() )
          t.matchedUserAgentName = 'ios-app';
        else if ( has( 'iphone' ) )
          t.matchedUserAgentName = 'iphone-unknown';
        else if ( has( 'ipad' ) )
          t.matchedUserAgentName = 'ipad-unknown';

        return t.matchedUserAgentName;
      },

      /**
       * This method detects the mobile platform name.
       */
      getPlatformName : function() {
        if ( t.matchedPlatformName !== false )
          return t.matchedPlatformName;

        if ( t.userAgent === false )
          return false;

        if ( has( 'windows ce' ) || has( 'windows phone' ) ) {
          t.matchedPlatformName = t.PLATFORM_WINDOWS;
        } else if ( has( 'ipad' ) ) {
          t.matchedPlatformName = t.PLATFORM_IPAD;
        } else if ( has( 'ipod' ) ) {
          t.matchedPlatformName = t.PLATFORM_IPOD;
        } else if ( has( 'iphone' ) ) {
          t.matchedPlatformName = t.PLATFORM_IPHONE;
        } else if ( has( 'android' ) ) {
          if ( t.isAndroidTablet() )
            t.matchedPlatformName = t.PLATFORM_ANDROID_TABLET;
          else
            t.matchedPlatformName = t.PLATFORM_ANDROID;
        } else if ( t.isKindleFire() ) {
          t.matchedPlatformName = t.PLATFORM_ANDROID_TABLET;
        } else if ( t.isBlackberry10() ) {
          t.matchedPlatformName = t.PLATFORM_BLACKBERRY_10;
        } else if ( has( 'blackberry' ) ) {
          t.matchedPlatformName = t.PLATFORM_BLACKBERRY;
        } else if ( t.isBlackberryTablet() ) {
          t.matchedPlatformName = t.PLATFORM_BLACKBERRY;
        } else if ( t.isSymbianPlatform() ) {
          t.matchedPlatformName = t.PLATFORM_SYMBIAN;
        } else if ( t.isSymbianS40Platform() ) {
          t.matchedPlatformName = t.PLATFORM_SYMBIAN_S40;
        } else if ( t.isJ2MEPlatform() ) {
          t.matchedPlatformName = t.PLATFORM_J2ME_MIDP;
        } else if ( t.isFirefoxOS() ) {
          t.matchedPlatformName = t.PLATFORM_FIREFOX_OS;
        } else if ( t.isFirefoxMobile() ) {
          t.matchedPlatformName = t.PLATFORM_MOBILE_GENERIC;
        }

        return t.matchedPlatformName;
      },


      /**
       * Detect the BlackBerry OS version.
       *
       * Note: This is for smartphones only. Does not work on BB tablets.
       */
      getBlackBerryOSVersion : check( function() {
        if ( t.isBlackberry10() )
          return '10';

        if ( ! has( 'blackberry' ) )
          return false;

        var rv = -1; // Return value assumes failure.
        var re;

        if ( has( 'webkit' ) ) { // Detecting the BB OS version for devices running OS 6.0 or higher
          re = /Version\/([\d\.]+)/i;
        } else {
          // BlackBerry devices <= 5.XX
          re = /BlackBerry\w+\/([\d\.]+)/i;
        }
        if ( re.exec( t.userAgent ) != null )
          rv =  RegExp.$1.toString();

        return rv === -1 ? false : rv;
      } ),

      /**
       * Detects if the current UA is iPhone Mobile Safari or another iPhone or iPod Touch Browser.
       */
      isIPhoneOrIPod : check( function() {
        return has( 'safari' ) && ( has( 'iphone' ) || has( 'ipod' ) );
      } ),

      /**
       * Detects if the current device is an iPad.
       */
      isIPad : check( function() {
        return has( 'ipad' ) && has( 'safari' );
      } ),


      /**
      *  Detects if the current UA is Chrome for iOS
      */
      isChromeForIOS : check( function() {
        return t.isIPhoneOrIPod() && has( 'crios/' );
      } ),

      /**
       * Detects if the current browser is the Native Android browser.
       */
      isAndroid : check( function() {
        if ( has( 'android' ) ) {
          return ! ( t.isOperaMini() || t.isOperaMobile() || t.isFirefoxMobile() );
        }
      } ),

      /**
       * Detects if the current browser is the Native Android Tablet browser.
       */
       isAndroidTablet : check( function() {
        if ( has( 'android' ) && ! has( 'mobile' ) ) {
          return ! ( t.isOperaMini() || t.isOperaMobile() || t.isFirefoxMobile() );
        }
      } ),


      /**
       * Detects if the current browser is Opera Mobile
       */
      isOperaMobile : check( function() {
        return has( 'opera' ) && has( 'mobi' );
      } ),

      /**
       * Detects if the current browser is Opera Mini
       */
      isOperaMini : check( function() {
        return has( 'opera' ) && has( 'mini' );
      } ),


      /**
       * isBlackberry10() can be used to check the User Agent for a BlackBerry 10 device.
       */
      isBlackberry10 : check( function() {
        return has( 'bb10' ) && has( 'mobile' );
      } ),

      /**
       * isBlackberryTablet() can be used to check the User Agent for a RIM blackberry tablet
       */
      isBlackberryTablet : check( function() {
        return has( 'playbook' ) && has( 'rim tablet' );
      } ),

      /**
       * Detects if the current browser is a Windows Phone 7 device.
       */
      isWindowsPhone7 : check( function () {
        return has( 'windows phone os 7' );
      } ),

      /**
       * Detects if the current browser is a Windows Phone 8 device.
       */
      isWindowsPhone8 : check( function () {
        return has( 'windows phone 8' );
      } ),

      /**
       * Detects if the device platform is J2ME.
       */
      isJ2MEPlatform : check( function () {
        return has( 'j2me/midp' ) || ( has( 'midp' ) && has( 'cldc' ) );
      } ),


      /**
       * Detects if the device platform is the Symbian Series 40.
       */
      isSymbianS40Platform : check( function() {
        if ( has( 'series40' ) ) {
          return has( 'nokia' ) || has( 'ovibrowser' ) || has( 'nokiabrowser' );
        }
      } ),


      /**
       * Detects if the device platform is the Symbian Series 60.
       */
      isSymbianPlatform : check( function() {
        if ( has( 'webkit' ) ) {
          // First, test for WebKit, then make sure it's either Symbian or S60.
          return has( 'symbian' ) || has( 'series60' );
        } else if ( has( 'symbianos' ) && has( 'series60' ) ) {
          return true;
        } else if ( has( 'nokia' ) && has( 'series60' ) ) {
          return true;
        } else if ( has( 'opera mini' ) ) {
          return has( 'symbianos' ) || has( 'symbos' ) || has( 'series 60' );
        }
      } ),


      /**
       * Detects if the current browser is the Kindle Fire Native browser.
       */
      isKindleFire : check( function() {
        return has( 'silk/' ) && has( 'silk-accelerated=' );
      } ),

      /**
       * Detects if the current browser is Firefox Mobile (Fennec)
       */
      isFirefoxMobile : check( function() {
        return has( 'fennec' );
      } ),


      /**
       * Detects if the current browser is the native FirefoxOS browser
       */
      isFirefoxOS : check( function() {
        return has( 'mozilla' ) && has( 'mobile' ) && has( 'gecko' ) && has( 'firefox' );
      } ),


      /**
       * Detects if the current UA is Facebook for iPad
       */
      isFacebookForIpad : check( function() {
        if ( ! has( 'ipad' ) )
          return false;

        return has( 'facebook' ) || has( 'fbforiphone' ) || has( 'fban/fbios;' );
      } ),

      /**
       * Detects if the current UA is Facebook for iPhone
       */
      isFacebookForIphone : check( function() {
        if ( ! has( 'iphone' ) )
          return false;

        return ( has( 'facebook' ) && ! has( 'ipad' ) ) ||
          ( has( 'fbforiphone' ) && ! has( 'tablet' ) ) ||
          ( has( 'fban/fbios;' ) && ! has( 'tablet' ) ); // FB app v5.0 or higher
      } ),

      /**
       * Detects if the current UA is Twitter for iPhone
       */
      isTwitterForIphone : check( function() {
        if ( has( 'ipad' ) )
          return false;

        return has( 'twitter for iphone' );
      } ),

      /**
       * Detects if the current UA is Twitter for iPad
       */
      isTwitterForIpad : check( function() {
        return has( 'twitter for ipad' ) || ( has( 'ipad' ) && has( 'twitter for iphone' ) );
      } ),


      /**
       * Detects if the current UA is WordPress for iOS
       */
      isWordPressForIos : check( function() {
        return has( 'wp-iphone' );
      } )
  };

  function has( str ) {
    return t.userAgent.indexOf( str ) != -1;
  }

  function check( fn ) {
    return function() {
      return t.userAgent === false ? false : fn() || false;
    }
  }

  g.wpcom_mobile_user_agent_info = t;

} )( typeof window !== 'undefined' ? window : this );
;
// listen for rlt authentication events and pass them to children of this document.
( function() {
	var currentToken;
	var parentOrigin;
	var iframeOrigins;
	var initializationListeners = [];
	var hasBeenInitialized = false;
	var RLT_KEY = 'jetpack:wpcomRLT';

	// IE11 compat version that doesn't require on `new URL( src )`
	function getOriginFromUrl( url ) {
		var parser = document.createElement('a');
		parser.href = url;
		return parser.origin;
	}

	// run on `load` for suitable iframes, this injects the current token if available
	function rltIframeInjector( event ) {
		if ( ! currentToken ) {
			return;
		}
		rltInjectToken( currentToken, event.target.contentWindow, getOriginFromUrl( event.target.src ) );
	}

	// run on DOMContentLoaded or later
	function rltMonitorIframes() {
		// wait until suitable iframes are loaded before trying to inject the RLT
		var iframes = document.querySelectorAll( "iframe" );
		for( var i=0; i<iframes.length; i++ ) {
			var iframe = iframes[i];
			if ( rltShouldAuthorizeIframe( iframe ) ) {
				iframe.addEventListener('load', rltIframeInjector);
			}
		}

		// listen for newly-created iframes, since some are injected dynamically
		var observer = new MutationObserver(function( mutationsList, observer ) {
			for(var i=0; i<mutationsList.length; i++) {
				var mutation = mutationsList[i];
				if (mutation.type === 'childList') {
					for(var j=0; j<mutation.addedNodes.length; j++) {
						var node = mutation.addedNodes[j];
						if (node instanceof HTMLElement && node.nodeName === 'IFRAME' && rltShouldAuthorizeIframe(node)) {
							node.addEventListener('load', rltIframeInjector);
						}
					}
				}
			}
		});

		observer.observe(document.body, { subtree: true, childList: true });
	}

	// should we inject RLT into this iframe?
	function rltShouldAuthorizeIframe( iframe ) {
		if ( ! Array.isArray( iframeOrigins ) ) {
			return;
		}
		return iframeOrigins.indexOf( getOriginFromUrl( iframe.src ) ) >= 0;
	}

	function rltInvalidateWindowToken( token, target, origin ) {
		if ( target && typeof target.postMessage === 'function' ) {
			try {
				target.postMessage( JSON.stringify( {
					type: 'rltMessage',
					data: {
						event: 'invalidate',
						token: token,
						sourceOrigin: window.location.origin,
					},
				} ), origin );
			} catch ( err ) {
				return;
			}
		}
	}

	/**
	 * PUBLIC METHODS
	 */
	window.rltInvalidateToken = function( token, sourceOrigin ) {
		// invalidate in current context
		if ( token === currentToken ) {
			currentToken = null;
		}

		// remove from localstorage, but only if in a top level window, not iframe
		try {
			if ( window.location === window.parent.location && window.localStorage ) {
				if ( window.localStorage.getItem(RLT_KEY) === token ) {
					window.localStorage.removeItem(RLT_KEY);
				}
			}
		} catch( e ) {
			console.info("localstorage access for invalidate denied - probably blocked third-party access", window.location.href);
		}

		// invalidate in iframes
		var iframes = document.querySelectorAll("iframe");
		for( var i=0; i<iframes.length; i++ ) {
			var iframe = iframes[i];
			var iframeOrigin = getOriginFromUrl( iframe.src );
			if ( iframeOrigin !== sourceOrigin && rltShouldAuthorizeIframe( iframe ) ) {
				rltInvalidateWindowToken( token, iframe.contentWindow, iframeOrigin );
			}
		}

		// invalidate in parent
		if ( parentOrigin && parentOrigin !== sourceOrigin && window.parent ) {
			rltInvalidateWindowToken( token, window.parent, parentOrigin );
		}
	}

	window.rltInjectToken = function( token, target, origin ) {
		if ( target && typeof target.postMessage === 'function' ) {
			try {
				target.postMessage( JSON.stringify( {
					type: 'loginMessage',
					data: {
						event: 'login',
						success: true,
						type: 'rlt',
						token: token,
						sourceOrigin: window.location.origin,
					},
				} ), origin );
			} catch ( err ) {
				return;
			}
		}
	};

	window.rltIsAuthenticated = function() {
		return !! currentToken;
	};

	window.rltGetToken = function() {
		return currentToken;
	};

	window.rltAddInitializationListener = function( listener ) {
		// if RLT is already initialized, call the listener immediately
		if ( hasBeenInitialized ) {
			listener( currentToken );
		} else {
			initializationListeners.push( listener );
		}
	};

	// store the token in localStorage
	window.rltStoreToken = function( token ) {
		currentToken = token;
		try {
			if ( window.location === window.parent.location && window.localStorage ) {
				window.localStorage.setItem( RLT_KEY, token );
			}
		} catch( e ) {
			console.info("localstorage access denied - probably blocked third-party access", window.location.href);
		}
	}

	window.rltInitialize = function( config ) {
		if ( ! config || typeof window.postMessage !== 'function' ) {
			return;
		}

		currentToken  = config.token;
		iframeOrigins = config.iframeOrigins;
		parentOrigin  = config.parentOrigin; // needed?

		// load token from localStorage if possible, but only in top level window
		try {
			if ( ! currentToken && window.location === window.parent.location && window.localStorage ) {
				currentToken = window.localStorage.getItem(RLT_KEY);
			}
		} catch( e ) {
			console.info("localstorage access denied - probably blocked third-party access", window.location.href);
		}

		// listen for RLT events from approved origins
		window.addEventListener( 'message', function( e ) {
			var message = e && e.data;
			if ( typeof message === 'string' ) {
				try {
					message = JSON.parse( message );
				} catch ( err ) {
					return;
				}
			}

			var type = message && message.type;
			var data = message && message.data;

			if ( type !== 'loginMessage' ) {
				return;
			}

			if ( data && data.type === 'rlt' && data.token !== currentToken ) {

				// put into localStorage if running in top-level window (not iframe)
				rltStoreToken( data.token );

				// send to allowlisted iframes
				var iframes = document.querySelectorAll("iframe");
				for( var i=0; i<iframes.length; i++ ) {
					var iframe = iframes[i];
					if ( rltShouldAuthorizeIframe( iframe ) ) {
						rltInjectToken( currentToken, iframe.contentWindow, getOriginFromUrl( iframe.src ) );
					}
				}

				// send to the parent, unless the event was sent _by_ the parent
				if ( parentOrigin && parentOrigin !== data.sourceOrigin && window.parent ) {
					rltInjectToken( currentToken, window.parent, parentOrigin );
				}
			}
		} );

		// listen for RLT events from approved origins
		window.addEventListener( 'message', function( e ) {
			var message = e && e.data;
			if ( typeof message === 'string' ) {
				try {
					message = JSON.parse( message );
				} catch ( err ) {
					return;
				}
			}

			var type = message && message.type;
			var data = message && message.data;

			if ( type !== 'rltMessage' ) {
				return;
			}

			if ( data && data.event === 'invalidate' && data.token === currentToken ) {
				rltInvalidateToken( data.token );
			}
		} );

		if ( iframeOrigins ) {
			if ( document.readyState !== 'loading' ) {
				rltMonitorIframes();
			} else {
				window.addEventListener( 'DOMContentLoaded', rltMonitorIframes );
			}
		}

		initializationListeners.forEach( function( listener ) {
			listener( currentToken );
		} );

		initializationListeners = [];

		hasBeenInitialized = true;
	};
} )();
;
( function () {
	window.addEventListener( 'message', function ( event ) {
		var allowed_origins = [ 'https://videopress.com', 'https://video.wordpress.com' ];
		if ( -1 === allowed_origins.indexOf( event.origin ) ) {
			return;
		}

		if ( event.data.event !== 'videopress_token_request' ) {
			return;
		}

		if ( ! window.videopressAjax ) {
			return;
		}

		var fetchData = {
			action: 'videopress-get-playback-jwt',
			guid: event.data.guid,
			post_id: window.videopressAjax.post_id || 0,
		};

		fetch( window.videopressAjax.ajaxUrl, {
			method: 'POST',
			credentials: 'same-origin',
			body: new URLSearchParams( fetchData ),
		} )
			.then( function ( response ) {
				if ( response.ok ) {
					return response.json();
				}
				throw Error( 'Response is not ok' );
			} )
			.then( function ( jsonResponse ) {
				if ( !! jsonResponse.success && jsonResponse.data ) {
					event.source.postMessage(
						{
							event: 'videopress_token_received',
							guid: fetchData.guid,
							jwt: jsonResponse.data.jwt,
						},
						'*'
					);
				} else {
					event.source.postMessage(
						{
							event: 'videopress_token_error',
							guid: fetchData.guid,
						},
						'*'
					);
				}
			} );
	} );
} )();
;
