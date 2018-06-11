    var NoticeManager = function () {
        this._vecObNotification = [];
    };

    NoticeManager.prototype = Object.create(NoticeManager.prototype);
    NoticeManager.prototype.constructor = NoticeManager;

    /**
    * 添加通知事件
    * @param {Node} node
    * @param {string} notifi
    * @param {function(string, string)} functionCallBack
    */
    NoticeManager.prototype.AddObNotification = function (node, notifi, functionCallBack) {
        if (node !== undefined && node !== null &&
            notifi !== undefined && notifi !== null && typeof notifi === 'string' &&
            functionCallBack !== undefined && functionCallBack !== null && typeof functionCallBack === 'function') {
            var nodeIndex = -1;
            for (var i = 0; i < this._vecObNotification.length; i++) {
                if (this._vecObNotification[i].Node === node) {
                    nodeIndex = i;
                    break;
                }
            }

            if (nodeIndex < 0) {
                nodeIndex = this._vecObNotification.length;
                this._vecObNotification[nodeIndex] = {
                    Node: node,
                    Data: []
                };
            }

            var notifiIndex = this._vecObNotification[i].Data.length;
            this._vecObNotification[i].Data[notifiIndex] = {
                Notifi: notifi,
                FunctionCall: functionCallBack
            };
        }
    };

    /**
    * 移除通知事件(notifi为空时将移除node上的所有通知)
    * @param {Node} node
    * @param {string} notifi
    */
    NoticeManager.prototype.RemoveObNotification = function (node, notifi) {
        if (node !== undefined && node !== null) {
            for (var i = 0; i < this._vecObNotification.length; i++) {
                if (this._vecObNotification[i].Node === node) {
                    if (notifi === undefined || notifi === null || typeof notifi !== 'string') {
                        this._vecObNotification.splice(i, 1);
                        break;
                    } else {
                        for (var j = 0; j < this._vecObNotification[i].Data.length; j++) {
                            if (this._vecObNotification[i].Data[j].Notifi === notifi) {
                                this._vecObNotification[i].Data.splice(j, 1);
                                break;
                            }
                        }

                        if (this._vecObNotification[i].Data.length === 0)
                            this._vecObNotification.splice(i, 1);
                    }
                    break;
                }
            }
        }
    };

    /**
    * 发送通知
    * @param {string} notifi
    * @param {string} notifiData
    */
    NoticeManager.prototype.PushNotification = function (notifi, notifiData) {
        if (notifi !== undefined && notifi !== null && typeof notifi === 'string') {
            for (var i = 0; i < this._vecObNotification.length; i++) {
                if (this._vecObNotification[i].Node !== null && this._vecObNotification[i].Data !== null) {
                    for (var j = 0; j < this._vecObNotification[i].Data.length; j++) {
                        if (this._vecObNotification[i].Data[j].Notifi !== null && this._vecObNotification[i].Data[j].FunctionCall !== null) {
                            if (this._vecObNotification[i].Data[j].Notifi === notifi) {
                                this._vecObNotification[i].Data[j].FunctionCall(notifi, notifiData);
                            }
                        }
                    }
                }
            }
        }
    };

    var g_NoticeManager = new NoticeManager();
    window.NoticeManager = g_NoticeManager;