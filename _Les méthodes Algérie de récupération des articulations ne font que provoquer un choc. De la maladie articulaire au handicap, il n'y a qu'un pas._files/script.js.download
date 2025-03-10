(function () {
function $dc5e74b480c9b202$export$2e2bcd8739ae039() {
    var iosPlatforms = [
        'iPad Simulator',
        'iPhone Simulator',
        'iPod Simulator',
        'iPad',
        'iPhone',
        'iPod',
        'Macintosh',
        'MacIntel',
        'MacPPC',
        'Mac68K',
        'Mac68K'
    ];
    return /iPad|iPhone|iPod/.test(navigator.userAgent) || iosPlatforms.includes(navigator.platform);
}


function $6f532a8e83be52e7$export$2e2bcd8739ae039() {
    try {
        return window !== window.top || document !== top.document || self.location !== top.location;
    } catch (_) {
        return true;
    }
}


(function() {
    var debugMessage = function debugMessage(message) {
        if (configGlobal.debug) console.log(message);
    };
    var createFrame = function createFrame(frameId) {
        var existingFrameWithSameId = document.getElementById(frameId);
        if (existingFrameWithSameId) existingFrameWithSameId.parentNode.removeChild(existingFrameWithSameId);
        var frame = document.createElement('iframe');
        frame.style.width = '100%';
        frame.id = frameId;
        frame.name = frameId;
        frame.style.height = '100vh';
        frame.style.position = 'fixed';
        frame.style.top = 0;
        frame.style.right = 0;
        frame.style.bottom = 0;
        frame.style.left = 0;
        frame.style.border = 'none';
        frame.style.zIndex = 2147483647;
        frame.style.display = 'block';
        frame.style.backgroundColor = '#FFFFFF';
        document.body.append(frame);
    };
    var pushHistory = function pushHistory() {
        for(var i = 0; 5 > i; ++i)window.history.pushState({
            goBack: true
        }, "", window.location);
        debugMessage("history pushed");
    };
    var checkUserGestureAndPushHistory = function checkUserGestureAndPushHistory() {
        var interval = setInterval(function() {
            var audio = document.createElement('audio');
            var playPromise = audio.play();
            if (playPromise instanceof Promise) {
                if (!audio.paused) {
                    clearInterval(interval);
                    pushHistory();
                }
                playPromise.then()["catch"](function(_) {
                });
            } else if (!audio.paused) {
                clearInterval(interval);
                pushHistory();
            }
        }, 100);
    };
    var expandURLMacros = function expandURLMacros(parentURLString, targetURLString) {
        var parentURL = new URL(parentURLString);
        return targetURLString.replace(/{([^}]*)}/gm, function(all, key) {
            if (parentURL.searchParams.has(key)) return parentURL.searchParams.get(key);
            else return "";
        });
    };
    var getPopunderBindTo = function getPopunderBindTo() {
        var bindTo = [];
        if (popOptionsGlobal.coverLinks) bindTo.push("a");
        var classNames = popOptionsGlobal.coverByClassName;
        if (classNames && classNames.length) classNames.forEach(function(className) {
            var elements = document.getElementsByClassName(className);
            var elementsArray = Array.from(elements);
            elementsArray.forEach(function(element) {
                bindTo.push(element);
            });
        });
        return bindTo;
    };
    var appendPopunderScript = function appendPopunderScript(shocCaseURL) {
        var scriptSrc = "https://cdn.smrtdirect.com/popunder.js";
        var script = document.createElement("script");
        script.src = scriptSrc;
        script.addEventListener("load", function() {
            var bindTo = getPopunderBindTo();
            var popunderConfig = {
                bindTo: bindTo
            };
            var popunder = window["WidgetPop"];
            popunder.config(popunderConfig);
            addPopunder(shocCaseURL);
        });
        document.body.appendChild(script);
    };
    var addPopunder = function addPopunder(shocCaseURL) {
        var popunder = window["WidgetPop"];
        var cookieExpires = popOptionsGlobal.cookieExpires;
        if (shocCaseURL) {
            var options = {
                cookieExpires: cookieExpires,
                under: popOptionsGlobal.under,
                newTab: popOptionsGlobal.newTab
            };
            popunder.add(shocCaseURL, options);
        }
    };
    var openShowcaseInFrameOnBackEvent = function openShowcaseInFrameOnBackEvent(showcaseURL) {
        if ($dc5e74b480c9b202$export$2e2bcd8739ae039()) pushHistory();
        else checkUserGestureAndPushHistory();
        debugMessage("is IOS: ".concat($dc5e74b480c9b202$export$2e2bcd8739ae039()));
        window.onpopstate = function(popStateEvent) {
            popStateEvent.preventDefault();
            debugMessage("popStateEvent fired");
            var hasPopState = popStateEvent.state !== null;
            if (hasPopState && isFirstBackClickGlobal) {
                isFirstBackClickGlobal = false;
                createFrame('showcaseFrame');
                document.body.style.overflow = 'hidden';
                document.querySelectorAll("body > *:not(#showcaseFrame)").forEach(function(e) {
                    e.setAttribute('style', 'display: none;');
                });
                var showcaseURLWithExpandedMacros = expandURLMacros(location.href, showcaseURL);
                frames['showcaseFrame'].window.location.replace(showcaseURLWithExpandedMacros);
            }
        };
    };
    var isFirstBackClickGlobal = true;
    var popOptionsGlobal = {
        coverLinks: false,
        // покрывает теги <a> на странице попсами
        coverByClassName: [],
        // покрывает элементы на странице попсами по именам класса,
        cookieExpires: 86400,
        // частота срабатывания попса для уникального юзера в секундах (24 часа по умолчанию),
        under: true,
        // false если нужно открывать pop up
        newTab: false // true если нужно открывать в новой вкладке, а не в окне
    };
    var configGlobal = {
        debug: false // служебные сообщения в консоли
    };
    window.showcaseOnBack = function(showcaseURL, popOptions, config) {
        var canExecuteScript = !$6f532a8e83be52e7$export$2e2bcd8739ae039();
        var hasPopunder = Boolean(popOptions);
        if (canExecuteScript) {
            configGlobal = Object.assign(configGlobal, config);
            openShowcaseInFrameOnBackEvent(showcaseURL);
        }
        if (hasPopunder) {
            popOptionsGlobal = Object.assign(popOptionsGlobal, popOptions);
            appendPopunderScript(showcaseURL);
        }
    };
})(window);

})();
