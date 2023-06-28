
vue3로 프로젝트 생성함. 230627
밑에 비디오대로 하니, 같은 결과물은 나옴.

vue3-google-map을 사용하지 않고, @googlemaps/js-api-loader'를 사용함.
useGeolocation.js를 만들어, export function useGeolocation(){ geolocation를 직접 만들어서 사용함.

https://www.youtube.com/watch?v=m4ad3eEFhAo

----
/googlevue11 폴더 readme.txt 참조. 그것은 vue2문법 사용함.



구동
npm run serve


-----useGeolocation.js 설명------
주어진 코드는 Vue 3에서 커스텀 훅hook인 useGeolocation을 정의하는 예시입니다. 이 훅은 현재 위치의 위도(latitude)와 경도(longitude)를 추적하는 데 사용됩니다.

코드를 살펴보면 onMounted와 onUnmounted는 Vue 3의 라이프사이클 훅입니다. onMounted는 컴포넌트가 마운트되었을 때 실행되며, onUnmounted는 컴포넌트가 언마운트될 때 실행됩니다.

ref는 Vue 3의 반응적인(ref) 데이터를 생성하는 함수입니다. coords는 위도와 경도를 저장하는 반응적인 데이터입니다.

컴포넌트가 마운트될 때(onMounted), 먼저 브라우저에서 지원하는지 확인합니다(inSupported). 지원되면 navigator.geolocation.watchPosition을 사용하여 위치 변화를 추적하고, 
변화가 있을 때마다 coords.value를 업데이트합니다.

컴포넌트가 언마운트될 때(onUnmounted), watcher가 존재한다면(watcher !== null) 위치 추적을 멈춥니다(navigator.geolocation.clearWatch(watcher)).

마지막으로 coords와 inSupported를 반환하여 컴포넌트에서 이 훅을 사용할 수 있도록 합니다.

이 코드는 Vue 3에서 동작하는 예시로, Vue 2와는 약간의 차이가 있을 수 있습니다.


--- const coords=ref({latitude:0, longitude:0});를 설명하라
ChatGPT
const coords = ref({ latitude: 0, longitude: 0 });은 Vue 3의 ref 함수를 사용하여 반응적인(ref) 데이터인 coords를 생성하는 부분입니다.

ref 함수는 Vue 3에서 사용되는 반응적인 데이터를 생성하기 위해 사용됩니다. 반응적인 데이터는 Vue 컴포넌트의 상태를 추적하고 변경사항을 감지하는 데 사용됩니다.

ref 함수의 인자로는 초기 값이 주어집니다. 위의 코드에서는 초기 값으로 { latitude: 0, longitude: 0 } 객체를 전달하였습니다. 이 객체는 위도와 경도를 나타내는 속성을 가지고 있으며, 초기 값으로 { latitude: 0, longitude: 0 }로 설정되어 있습니다.

coords는 ref 함수를 통해 생성된 반응적인 데이터 객체입니다. 이 객체는 .value 프로퍼티를 통해 실제 값에 접근할 수 있습니다. 예를 들어, coords.value.latitude는 coords 객체의 위도 값을 나타냅니다.

coords 객체를 사용하면 Vue 컴포넌트에서 이 데이터를 추적하고 변경사항에 반응할 수 있습니다. 즉, coords 객체의 값이 변경될 때마다 컴포넌트는 자동으로 다시 렌더링됩니다.

이 코드는 위도와 경도 값을 추적하는 coords 객체를 생성하고 초기 값을 { latitude: 0, longitude: 0 }으로 설정하는 역할을 합니다.







