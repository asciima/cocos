    //使用promise封装Ajax
    window.getRequest = function (url) {
        return new Promise( (resolve, reject) => {
            var xhr = new XMLHttpRequest()
            xhr.open('GET', url, true)
            xhr.onreadystatechange = function () {
                if (this.readyState === 4) {
                    if (this.status === 200) {
                        resolve(this.responseText, this)
                    } else {
                        var resJson = { code: this.status, response: this.response }
                        reject(resJson, this)
                    }
                }
            }
            xhr.send()
        })

    }

    window.postRequest = function (url, data) {
        console.log('post请求参数',data)
        return new Promise( (resolve, reject) => {
            var xhr = new XMLHttpRequest()
            xhr.open("POST", url, true)
            xhr.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
            xhr.onreadystatechange = function () {
                if (this.readyState === 4) {
                    if (this.status === 200) {
                        // console.log('request请求成功',this.responseText)
                        resolve(JSON.parse(this.responseText), this)
                    } else {
                        var resJson = { code: this.status, response: this.response }
                        reject(resJson, this)
                    }
                }
            }
            xhr.send(data)
        })
    }

    //无论promise对象最后状态如何都会执行
    Promise.prototype.finally = function (callback) {
    let P = this.constructor;
    return this.then(
        value => P.resolve(callback()).then(() => value),
        reason => P.resolve(callback()).then(() => { throw reason })
    );
    };


