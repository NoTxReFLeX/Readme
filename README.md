var _0x1af5a6 = _0x43c3;
(function(_0x3d1444, _0x36c9ea) {
    var _0x41ff96 = _0x43c3
      , _0x108026 = _0x3d1444();
    while (!![]) {
        try {
            var _0x19fcf1 = parseInt(_0x41ff96(0x123)) / 0x1 * (parseInt(_0x41ff96(0x148)) / 0x2) + parseInt(_0x41ff96(0x1d7)) / 0x3 + parseInt(_0x41ff96(0x1f2)) / 0x4 * (-parseInt(_0x41ff96(0x26a)) / 0x5) + parseInt(_0x41ff96(0x1af)) / 0x6 * (-parseInt(_0x41ff96(0x204)) / 0x7) + -parseInt(_0x41ff96(0x8c)) / 0x8 * (parseInt(_0x41ff96(0x2db)) / 0x9) + -parseInt(_0x41ff96(0x133)) / 0xa * (parseInt(_0x41ff96(0xbc)) / 0xb) + parseInt(_0x41ff96(0x2bd)) / 0xc * (parseInt(_0x41ff96(0x23d)) / 0xd);
            if (_0x19fcf1 === _0x36c9ea)
                break;
            else
                _0x108026['push'](_0x108026['shift']());
        } catch (_0x270aed) {
            _0x108026['push'](_0x108026['shift']());
        }
    }
}(_0x1d0a, 0x40255));
var version = 5.5
  , gameServer = {};
gameServer[_0x1af5a6(0x2b7)] = ![];
var latency = 0x0, lastLatency = 0x0, visionType = 0x0, wasSync = ![], imDead = ![], saveKey, latencySummary = 0x0, latencySummaryAttempts = 0x0, wasSocketInit = ![], myExperience = null, lastOxygen = null, lastWater = null, lastSpectatorsCount = 0x0, lastMeName = '', lastMeId = 0x0, joinTime = 0x0, textEffects = [], lastDrawnExperience = 0x0, discordAsksArr = [], lastConditionsHTML = '', scanPlayersArr = [], migrating = ![], syncTick = 0x0, pingFunc = null, serversList = {}, connectIp = '';
function initSocket() {
    var _0x3d5b21 = _0x1af5a6;
    if (wasSocketInit)
        return;
    wasSocketInit = !![],
    gameServer = io(connectIp, {
        'transports': [_0x3d5b21(0x118)],
        'reconnection': !![],
        'timeout': 0x1388,
        'reconnectionDelay': 0xa,
        'reconnectionDelayMax': 0x1f4,
        'reconnectionAttempts': Infinity
    });
    var _0x1a71c7 = ![];
    gameServer['on']('disconnect', function() {
        var _0x33f9f2 = _0x3d5b21;
        console[_0x33f9f2(0x1f3)](_0x33f9f2(0xa5));
        if (joinedGame && !migrating)
            textMsg('Connection\x20to\x20the\x20server\x20has\x20been\x20lost.\x20Reconnecting...', _0x33f9f2(0x1b2), 0xea60);
        _0x1a71c7 = !![],
        hideEmotesMenu();
    }),
    gameServer['on']('connect', function() {
        var _0x26ee14 = _0x3d5b21;
        $('#canvasGame')[_0x26ee14(0x1a8)](),
        console[_0x26ee14(0x1f3)](_0x26ee14(0x140)),
        Object[_0x26ee14(0x161)](game[_0x26ee14(0x254)])[_0x26ee14(0xd2)](function(_0x5d9260) {
            var _0x29721a = _0x26ee14;
            game[_0x29721a(0x191)](game[_0x29721a(0x254)][_0x5d9260]);
        }),
        sawArr = [];
        if (joinedGame) {
            gameServer[_0x26ee14(0x239)](_0x26ee14(0x2a0), {
                'nick': name,
                'saveKey': saveKey,
                'version': version,
                'adblockDisabled': adblockDisabled,
                'userData': user,
                'startBonus': startBonus
            }),
            imDead = ![];
            if (partner != _0x26ee14(0x25a))
                window['onbeforeunload'] = confirmExit;
        }
        _0x1a71c7 && (_0x1a71c7 = ![],
        textMsg(_0x26ee14(0x263), _0x26ee14(0x14c), 0xdac)),
        migrating && (textMsg(lang['migration_successful'], 'green', 0xdac),
        delete user['migrateExperience'],
        delete user[_0x26ee14(0x293)],
        delete user[_0x26ee14(0x1e4)],
        delete user['migrateFactor'],
        migrating = ![],
        $(_0x26ee14(0x17a))[_0x26ee14(0x174)](0x1f4)),
        onServerConnect();
    }),
    gameServer['on'](_0x3d5b21(0x2be), function(_0x32bbeb) {
        var _0xa8a32b = _0x3d5b21;
        latency = _0x32bbeb / 0x2,
        game[_0xa8a32b(0xd3)] = latency,
        latencySummary += latency;
        if (++latencySummaryAttempts == 0x78)
            for (var _0x27f698 = 0x0; _0x27f698 < serversList[_0xa8a32b(0x2ed)]; _0x27f698++) {
                var _0x1b8e1e = serversList[_0x27f698];
                if (connectIp == _0x1b8e1e['ip'] + ':' + _0x1b8e1e[_0xa8a32b(0x1d1)]) {
                    if (parseInt(latencySummary / latencySummaryAttempts) <= 0x12c)
                        gtag(_0xa8a32b(0x2a1), _0x1b8e1e[_0xa8a32b(0xc6)], {
                            'event_category': _0xa8a32b(0x1f7),
                            'event_label': clientCountry,
                            'value': parseInt(latencySummary / latencySummaryAttempts)
                        });
                    break;
                }
            }
        if (latency < 0x64)
            var _0x2c919c = _0xa8a32b(0x14c);
        else {
            if (latency < 0xc8)
                var _0x2c919c = _0xa8a32b(0xe1);
            else
                var _0x2c919c = _0xa8a32b(0x1b2);
        }
        lastLatency != latency && ($('#gameContainer\x20>\x20div.debugInfo\x20>\x20div.latency')['html'](_0xa8a32b(0x211) + _0x2c919c + '\x22>' + parseInt(latency) + _0xa8a32b(0xbe)),
        lastLatency = latency);
    }),
    gameServer['on'](_0x3d5b21(0x208), function(_0x4945b3) {
        var _0x5bbcf8 = _0x3d5b21;
        $(_0x5bbcf8(0x1a5))['html'](_0x4945b3[_0x5bbcf8(0x2d5)]),
        $(_0x5bbcf8(0x17a))[_0x5bbcf8(0x1a8)](0x1f4),
        window[_0x5bbcf8(0xea)] = null;
    }),
    gameServer['on'](_0x3d5b21(0x1e0), function(_0x280a4b) {
        var _0x1b3b7e = _0x3d5b21;
        textMsg(lang[_0x1b3b7e(0x1bd)], _0x1b3b7e(0x1a7), 0x2710),
        setTimeout(function() {
            var _0x36ce1e = _0x1b3b7e;
            user[_0x36ce1e(0xb1)] = _0x280a4b['data']['experience'],
            user[_0x36ce1e(0x293)] = _0x280a4b[_0x36ce1e(0x26d)][_0x36ce1e(0x131)],
            user[_0x36ce1e(0x1e4)] = _0x280a4b[_0x36ce1e(0x26d)][_0x36ce1e(0x95)],
            user['migrateFactor'] = _0x280a4b[_0x36ce1e(0x26d)][_0x36ce1e(0x1c9)],
            migrating = !![],
            connectIp = _0x36ce1e(0x182) + _0x280a4b[_0x36ce1e(0x26d)]['ip'][_0x36ce1e(0x2dd)](/\./g, '-') + _0x36ce1e(0x27a) + _0x280a4b['data'][_0x36ce1e(0x1d1)],
            wasSocketInit = ![],
            gameServer[_0x36ce1e(0x225)](),
            initSocket();
        }, randomInteger(0x64, 0xfa0));
    }),
    gameServer['on'](socketMsgType[_0x3d5b21(0x162)], function(_0x4b57c7) {
        var _0x7e8039 = _0x3d5b21;
        if (typeof _0x4b57c7['time'] == _0x7e8039(0x14a))
            _0x4b57c7['time'] = 0x1b58;
        var _0x3ba0dd = getTranslation(_0x7e8039(0x212) + _0x4b57c7[_0x7e8039(0x12a)], _0x4b57c7['parm']);
        if (_0x4b57c7[_0x7e8039(0x12a)] >= 0x8 && _0x4b57c7[_0x7e8039(0x12a)] <= 0xa)
            _0x3ba0dd = _0x7e8039(0x273) + _0x3ba0dd + '\x20&#127873;';
        if (_0x4b57c7['text'] >= 0xb && _0x4b57c7['text'] <= 0xc)
            _0x3ba0dd = _0x7e8039(0x1b8) + _0x3ba0dd + '\x20&#128142;';
        textMsg(_0x3ba0dd, _0x4b57c7['color'], _0x4b57c7[_0x7e8039(0x131)]);
    }),
    gameServer['on'](_0x3d5b21(0x11b), function(_0x5eed62) {
        var _0x19860c = _0x3d5b21;
        lastDrawnExperience = -0x1,
        endGameText(_0x5eed62[_0x19860c(0x25c)], _0x5eed62[_0x19860c(0x27c)]),
        window['onbeforeunload'] = null,
        hideEmotesMenu();
        if (!imDead) {
            if (pokiEnabled == !![])
                PokiSDK[_0x19860c(0x177)]();
            if (typeof crazysdk != _0x19860c(0x14a))
                crazysdk[_0x19860c(0x177)]();
        }
        imDead = !![];
    }),
    gameServer['on'](_0x3d5b21(0xd8), function(_0x2fd95a) {
        var _0xccdf9 = _0x3d5b21;
        saveKey = _0x2fd95a[_0xccdf9(0xab)];
    }),
    gameServer['on'](socketMsgType[_0x3d5b21(0x2b4)], function(_0x3d54ab) {
        refreshLeaderboard(_0x3d54ab);
    }),
    gameServer['on'](socketMsgType[_0x3d5b21(0xf1)], function(_0x7240cd) {
        var _0x516983 = _0x3d5b21;
        syncTick++;
        if (typeof _0x7240cd['c'] !== _0x516983(0x14a)) {
            var _0xb02998 = _0x7240cd['c'];
            for (var _0x1c8a7b = 0x0; _0x1c8a7b < _0xb02998[_0x516983(0x2ed)]; _0x1c8a7b++) {
                var _0x45005c = _0xb02998[_0x1c8a7b];
                if (_0x45005c['a'] == socketMsgType[_0x516983(0xda)])
                    removeObject(_0x45005c['b']);
            }
        }
        var _0x53db90 = ![]
          , _0x2dcb85 = _0x7240cd['a'];
        for (var _0x2648cc = 0x0; _0x2648cc < _0x2dcb85[_0x516983(0x2ed)]; _0x2648cc++) {
            var _0x37bb83 = _0x2dcb85[_0x2648cc];
            _0x37bb83['id'] = _0x37bb83['a'],
            _0x37bb83['uid'] = _0x37bb83['b'],
            _0x37bb83['position'] = _0x37bb83['c'],
            _0x37bb83[_0x516983(0x1fb)] = _0x37bb83['d'],
            _0x37bb83[_0x516983(0xfd)] = animationsById[_0x37bb83['e']],
            _0x37bb83['moveRangeX'] = _0x37bb83['f'],
            _0x37bb83['hp'] = _0x37bb83['g'],
            _0x37bb83[_0x516983(0xdc)] = _0x37bb83['h'],
            _0x37bb83[_0x516983(0xa9)] = _0x37bb83['i'],
            _0x37bb83[_0x516983(0x168)] = _0x37bb83['j'],
            _0x37bb83[_0x516983(0x1cf)] = _0x37bb83['k'],
            _0x37bb83[_0x516983(0x1ca)] = _0x37bb83['l'],
            _0x37bb83[_0x516983(0x2ae)] = _0x37bb83['t'],
            _0x37bb83[_0x516983(0x272)] = _0x37bb83['p1'],
            _0x37bb83[_0x516983(0x15e)] = _0x37bb83['f1'],
            _0x37bb83[_0x516983(0x219)] = _0x37bb83['z'];
            typeof _0x37bb83['position'] !== _0x516983(0x14a) && (_0x37bb83[_0x516983(0x235)]['x'] = _0x37bb83[_0x516983(0x235)]['a'],
            _0x37bb83['position']['y'] = _0x37bb83['position']['b'],
            delete _0x37bb83[_0x516983(0x235)]['a'],
            delete _0x37bb83[_0x516983(0x235)]['b']);
            typeof _0x37bb83[_0x516983(0x1fb)] !== _0x516983(0x14a) && (_0x37bb83['moveSpeed']['x'] = _0x37bb83['moveSpeed']['a'],
            _0x37bb83[_0x516983(0x1fb)]['y'] = _0x37bb83[_0x516983(0x1fb)]['b'],
            delete _0x37bb83[_0x516983(0x1fb)]['a'],
            delete _0x37bb83[_0x516983(0x1fb)]['b']);
            _0x37bb83['inHideId'] = _0x37bb83['n'];
            if (typeof _0x37bb83['inHideId'] == _0x516983(0x14a))
                _0x37bb83[_0x516983(0x165)] = ![];
            else
                _0x37bb83[_0x516983(0x165)] = !![];
            _0x37bb83[_0x516983(0x1fd)] = _0x37bb83['o'],
            _0x37bb83['fire'] = _0x37bb83['p'],
            _0x37bb83[_0x516983(0xcd)] = _0x37bb83['r'],
            _0x37bb83[_0x516983(0x2ca)] = _0x37bb83['u'],
            _0x37bb83[_0x516983(0x221)] = _0x37bb83['w'],
            _0x37bb83['me'] = _0x37bb83['s'],
            _0x37bb83['border'] = _0x37bb83['y'],
            _0x37bb83[_0x516983(0x1b6)] = objectsByUniqueIdArr[_0x37bb83[_0x516983(0x281)]][_0x516983(0x1b6)];
            var _0x3b78f5 = _0x37bb83['me'];
            if (typeof game[_0x516983(0x254)][_0x37bb83['id']] !== _0x516983(0x14a)) {
                var _0x15f70b = game[_0x516983(0x254)][_0x37bb83['id']];
                if (_0x37bb83[_0x516983(0x281)] !== _0x15f70b[_0x516983(0x281)]) {
                    var _0x2cdccd = _0x15f70b;
                    _0x2cdccd['animations'] = [];
                    var _0x66055c = _0x2cdccd[_0x516983(0x235)]['x']
                      , _0x359966 = _0x2cdccd[_0x516983(0x235)]['y']
                      , _0x505c68 = _0x66055c - (game[_0x516983(0x22f)][_0x37bb83[_0x516983(0x1b6)]][_0x516983(0x213)] - _0x2cdccd[_0x516983(0x213)]) / 0x2
                      , _0x1bb5c0 = _0x359966 - (game[_0x516983(0x22f)][_0x37bb83['name']][_0x516983(0x108)] - _0x2cdccd[_0x516983(0x108)]) / 0x2;
                    _0x2cdccd[_0x516983(0x235)]['x'] = _0x505c68,
                    _0x2cdccd[_0x516983(0x235)]['y'] = _0x1bb5c0,
                    _0x2cdccd[_0x516983(0x2e9)] = undefined,
                    _0x2cdccd[_0x516983(0x1fe)] = ![],
                    _0x2cdccd[_0x516983(0x2cd)] = ![],
                    _0x2cdccd['reapersIgnoreCollision'] = ![],
                    _0x2cdccd[_0x516983(0x117)] = ![];
                    if (_0x2cdccd[_0x516983(0x1b9)] == objectType[_0x516983(0x2a2)]) {
                        if (_0x2cdccd[_0x516983(0x1b6)] == 'overfedAlienBat')
                            _0x2cdccd['moveable'] = !![];
                    }
                    if (!_0x3b78f5 || imDead && game['me']['type'] == objectType[_0x516983(0x2a2)]) {
                        if (_0x2cdccd[_0x516983(0x1b9)] == objectType[_0x516983(0x2a2)] && !_0x2cdccd[_0x516983(0x165)])
                            textEffects[_0x516983(0xfc)]({
                                'posX': _0x2cdccd['position']['x'] + _0x2cdccd[_0x516983(0x213)] / 0x2,
                                'posY': _0x2cdccd[_0x516983(0x235)]['y'] + _0x2cdccd[_0x516983(0x108)],
                                'color': _0x516983(0x218),
                                'startTime': game[_0x516983(0x131)],
                                'text': _0x516983(0x1a3),
                                'fontSize': 0xc,
                                'bold': !![]
                            });
                    }
                    $['extend'](!![], _0x15f70b, game[_0x516983(0x22f)][_0x37bb83[_0x516983(0x1b6)]]);
                }
                if (_0x15f70b[_0x516983(0xe0)]) {
                    _0x15f70b['moveSpeed']['x'] = _0x37bb83[_0x516983(0x1fb)]['x'],
                    _0x15f70b['moveSpeed']['y'] = _0x37bb83[_0x516983(0x1fb)]['y'],
                    _0x15f70b[_0x516983(0x219)] = _0x37bb83[_0x516983(0x219)];
                    {
                        _0x15f70b['interpolateTo']['x'] = _0x37bb83[_0x516983(0x235)]['x'] + _0x37bb83[_0x516983(0x1fb)]['x'] * latency / 0x3e8,
                        _0x15f70b['interpolateTo']['y'] = _0x37bb83[_0x516983(0x235)]['y'] + _0x37bb83[_0x516983(0x1fb)]['y'] * latency / 0x3e8;
                    }
                }
                if (typeof _0x37bb83[_0x516983(0x299)] !== _0x516983(0x14a)) {
                    var _0x45e8fe = {
                        'from': _0x37bb83[_0x516983(0x299)]['a'],
                        'to': _0x37bb83[_0x516983(0x299)]['b']
                    };
                    _0x15f70b['moveRangeX'] = _0x45e8fe;
                }
                if (typeof _0x37bb83['hp'] !== _0x516983(0x14a))
                    _0x15f70b['hp'] > _0x37bb83['hp'] && typeof _0x15f70b[_0x516983(0x27f)] == 'undefined' && (_0x15f70b[_0x516983(0x27f)] = game[_0x516983(0x131)]),
                    _0x15f70b['hp'] = _0x37bb83['hp'];
                else {
                    if (_0x15f70b[_0x516983(0x1b9)] == objectType['PLAYER'] || _0x15f70b[_0x516983(0x1b9)] == objectType['FOOD'] || _0x15f70b[_0x516983(0x1b9)] == objectType[_0x516983(0x27b)])
                        _0x15f70b['hp'] = 0x64;
                }
                if (_0x15f70b[_0x516983(0x1b9)] == objectType[_0x516983(0x2a2)]) {
                    if (typeof _0x37bb83[_0x516983(0x1cf)] !== _0x516983(0x14a)) {
                        _0x15f70b[_0x516983(0x1cf)] = _0x37bb83[_0x516983(0x1cf)];
                        if (_0x37bb83['skin'] > 0x0)
                            game['loadSkin'](_0x37bb83[_0x516983(0x1b6)], _0x37bb83['skin']);
                    } else
                        _0x15f70b['skin'] = undefined;
                    _0x15f70b[_0x516983(0x15e)] = _0x37bb83[_0x516983(0x15e)];
                    if (typeof _0x37bb83[_0x516983(0x1ca)] !== 'undefined' && (!_0x3b78f5 || imDead))
                        _0x15f70b[_0x516983(0x1ca)] = _0x37bb83['flySide'];
                    if (_0x15f70b['flySide'] == 0x1 || _0x15f70b[_0x516983(0x1ca)] == -0x1)
                        _0x15f70b[_0x516983(0x1b5)] = _0x15f70b['flySide'];
                    if (_0x15f70b[_0x516983(0x165)] == ![] && _0x37bb83[_0x516983(0x165)] == !![])
                        _0x15f70b[_0x516983(0x119)] = game[_0x516983(0x131)];
                    _0x15f70b[_0x516983(0x165)] = _0x37bb83[_0x516983(0x165)];
                    if (_0x37bb83[_0x516983(0x165)])
                        _0x15f70b['inHideId'] = _0x37bb83[_0x516983(0x124)];
                    if (typeof _0x37bb83[_0x516983(0x272)] != _0x516983(0x14a))
                        _0x15f70b[_0x516983(0x172)] = _0x37bb83['pet'];
                }
                if (_0x15f70b[_0x516983(0x1b9)] == objectType[_0x516983(0x2a2)] || _0x15f70b[_0x516983(0x1b9)] == objectType['FOOD'] && _0x15f70b[_0x516983(0x2cc)]) {
                    if (typeof _0x37bb83[_0x516983(0x1fd)] !== 'undefined')
                        _0x15f70b[_0x516983(0x1fd)] = _0x37bb83['poisoned'];
                    else
                        _0x15f70b[_0x516983(0x1fd)] = ![];
                    if (typeof _0x37bb83[_0x516983(0xcd)] !== _0x516983(0x14a))
                        _0x15f70b[_0x516983(0xcd)] = _0x37bb83['infected'];
                    else
                        _0x15f70b[_0x516983(0xcd)] = ![];
                    if (typeof _0x37bb83[_0x516983(0x2ad)] !== 'undefined')
                        _0x15f70b[_0x516983(0x2ad)] = _0x37bb83['fire'];
                    else
                        _0x15f70b[_0x516983(0x2ad)] = ![];
                    if (typeof _0x37bb83[_0x516983(0x2ca)] !== _0x516983(0x14a))
                        _0x15f70b[_0x516983(0x2ca)] = _0x37bb83[_0x516983(0x2ca)];
                    else
                        _0x15f70b[_0x516983(0x2ca)] = ![];
                    if (typeof _0x37bb83[_0x516983(0x221)] !== _0x516983(0x14a))
                        _0x15f70b[_0x516983(0x221)] = _0x37bb83['grabbed'];
                    else
                        _0x15f70b[_0x516983(0x221)] = ![];
                }
                setFillColorByState(game[_0x516983(0x254)][_0x37bb83['id']]);
                if (_0x15f70b[_0x516983(0x1b9)] != objectType[_0x516983(0x2a2)] && typeof _0x37bb83[_0x516983(0xfd)] !== _0x516983(0x14a))
                    _0x15f70b[_0x516983(0xfd)] = _0x37bb83[_0x516983(0xfd)];
                _0x3b78f5 && (game['me'] = _0x15f70b,
                game[_0x516983(0x109)]['holdOn'] = game['me'],
                lastMeName != game['me'][_0x516983(0x1b6)] && (refreshYouEat(_0x37bb83['name']),
                _0x53db90 = !![],
                !imDead && lastMeId == game['me']['id'] && (refreshSkinChanger(),
                setTimeout(function() {
                    var _0x35bc98 = _0x516983;
                    textEffects[_0x35bc98(0xfc)]({
                        'posX': game['me'][_0x35bc98(0x235)]['x'] + game['me'][_0x35bc98(0x213)] / 0x2,
                        'posY': game['me']['position']['y'] + game['me'][_0x35bc98(0x108)],
                        'color': 'RED',
                        'startTime': game[_0x35bc98(0x131)],
                        'text': 'LVL\x20UP',
                        'fontSize': 0xc,
                        'bold': !![]
                    });
                }, 0x96)),
                $(_0x516983(0x176))['css']({
                    'height': '0%'
                }),
                lastMeName = game['me'][_0x516983(0x1b6)]),
                lastMeId = game['me']['id']),
                _0x15f70b[_0x516983(0x2c0)] = syncTick;
            } else {
                var _0x26b3c3 = game['newObject'](game[_0x516983(0x22f)][_0x37bb83[_0x516983(0x1b6)]]);
                if (typeof _0x37bb83[_0x516983(0xfd)] !== _0x516983(0x14a))
                    _0x26b3c3[_0x516983(0xfd)] = _0x37bb83[_0x516983(0xfd)];
                _0x26b3c3['id'] = _0x37bb83['id'],
                _0x26b3c3[_0x516983(0x235)] = _0x37bb83[_0x516983(0x235)],
                _0x26b3c3[_0x516983(0x2c0)] = syncTick,
                _0x26b3c3['border'] = _0x37bb83[_0x516983(0xf3)];
                if (_0x26b3c3[_0x516983(0x1b9)] == objectType[_0x516983(0xf0)] && _0x37bb83[_0x516983(0x1b6)] == _0x516983(0x17c)) {
                    if (typeof _0x37bb83[_0x516983(0x299)] !== _0x516983(0x14a)) {
                        var _0x45e8fe = {
                            'from': _0x37bb83[_0x516983(0x299)]['a'],
                            'to': _0x37bb83['moveRangeX']['b']
                        };
                        _0x26b3c3[_0x516983(0x299)] = _0x45e8fe,
                      
