# REACT
## react-router-dom 'history'

Router로 컴포넌트의 Path와 라우팅할 컴포넌트를 정해줄 수 있는데, 해당하는 라우터는 props를 통해 history 객체를 전달받게 된다.
history 객체를 콘솔로 찍어보면 아래와 같이 goBack(), goForward() 등 앞/뒤로 이동할 수 있는 메소드 뿐만 아니라 다양한 메소드와 관련 객체들이 존재다.
이 중 라우팅 변경을 위해 가장 빈번히 사용되는 메소드가 push()인데, history.push('이동하고자 하는 path') 를 통해 원하는 컴포넌트로 이동이 가능하다.


``` javascript
import { useHistory } from "react-router-dom";
...
let history = useHistory();
history.push('path');
history.goBack();
```
#### Redirect / history.push
``` javascript
// 렌더링하면 새 location으로 이동.
// server-side redirects do
// current location in the history stack
<Redirect to='/path' />

// pushes a new entey onto history stack
history.push('/path');
```