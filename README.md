# webm-to-wav-converter

Converts a auido/webm blob to a audio/wav blob

## Use your own logic for recording and Get the Audio Blob (`audio/wav`)

<br/>

```javascript
import { WebmToWavConverter } from 'webm-to-wav-converter';

const constraints = { audio: true, video: false };

try {
	const stream = await navigator.mediaDevices.getUserMedia(constraints);

	const mediaRecorder = new MediaRecorder(stream);

	const data = [];

	mediaRecorder.ondataavailable = (e) => e.data.size && data.push(e.data);

	mediaRecorder.onstop = () => {
		// For 16-bit audio
		const wavBlob = WebmToWavConverter(data, false);

		// For 32-bit audio
		const wavBlob = WebmToWavConverter(data, true);
	};
} catch (err) {
	console.error(err);
}
```
