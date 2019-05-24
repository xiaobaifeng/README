##  扩充自然语言识别方言的（SDK）： 
	
	前端功能 ---- 自然语言导航
			 |
		支持语音操作的页面
			 |
		 实时补充语言导航
			 |
         完善语音识别

这个再进一步不就是
	
	期望：图片预览功能
	
	语音识别 ——>  语音导航 ——> 具体对应的功能（会不会代码就不重要了）

##  js数字转二进制

```bash
	function twoJZ (num, curtwoJZ) {
		var _curtwoJZ = curtwoJZ || '',
			shang = Math.floor(num / 2),
			yu = num % 2;
		return shang !== 0  ? twoJZ(shang, yu + _curtwoJZ) : yu + _curtwoJZ 
	}
```
