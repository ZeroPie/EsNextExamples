# esnextstuff




```js
const list = ['1st', 8, 9, 10]

const getHead = ([head]) => head  // ( ͡° ͜ʖ ͡°)  
const getTail = ([, ...tail]) => tail

const allButtFirst = getTail(list);
const firstEle = getHead(list);
```

things going on there...
1. const
1. Destructuring/Spreading
1. Arrow functions
1. Implicit return in arrow functions
1. ( ͡° ͜ʖ ͡°) 





!! const (cannot be reassigned but is mutable)

```js
const nevaGonnaChange = [1,2];

nevaGonnaChange.map(i => console.log(` I will never change ${i}`))

nevaGonnaChange[0] = 0
nevaGonnaChange[1] = 0

nevaGonnaChange.map(i => console.log(` wait wat? ${i}`))
```


Destructuring:


```
const pileOfGoo = {
  goo: 'goo',
  isToxic: true,
  name: 'pileOfGoo'
}

const randomUser = {
  name: 'Jack'
}

export const createUser = ({
  name = "NoName",
  isToxic = '',
  fetishes = {},
  photoURL = ""
} = {}) => ({
  name,
  private: {
    fetishes: {}
  },
  photoURL
})
```

2.Spreading:
```js
    const a = [1,2,3];
    const b = [...a, 4, 5]
```

Var dumping in destructuring 
```
  const list = ['1st', 8, 9, 10]
  const getTail = ([, ...tail]) => tail
```


Return a copy
```js
    const invertArray = array => [...array].reverse();
````


A Real World Example

```js
export const doGetUserByUid = async uid =>
    firestore
        .collection("users")
        .doc(uid)
        .get()
        .then(doc => doc.data())

export const doGetUserProfileByUid = async uid => {    
      let publicData = await doGetUserByUid(uid)
      let privateData = await doGetPrivateDataFromUser(uid)
      let allData = {...publicData, ...privateData}
      let userProfile =  PrivateProfile(allData)
      return userProfile
}
```

1) Arrow Functions
2) async Await
3) implicit Returns
4) promises
5) gathering/spread



``` js
import ChatMessage from "../../Molecules/ChatMessage/ChatMessage";

export const Conversation = ({ senderId, messages }) => {
    const getMessageContent = ({ parts : [{payload : {content}} = {}] = []}) => content
    const isReceiver = id => senderId === id ? 'left' : 'right'

    return (
        <Fragment>
          { messages.map((message,i) => 
              <ChatMessage key={i} 
                position={isReceiver(message.senderId)} 
                userName={message.senderId} 
                createdAt={message.createdAt}
                text={getMessageContent2(message)}/>
            )
          }
        </Fragment>
    )
}

export default Conversation
```

Other Real World Stuff

```js
export const doGetDevsFromFirestore = () =>
    firestore
        .collection("users")
        .where("isDev", "==", true)
        .get()
        .then(snapshot =>
            snapshot.docs.map(documentSnapshot => documentSnapshot.data())
        )
```

1. implicit return of a promise
2. use `map` to return a new array with the result of calling a function on each element

```js
export const doGetUserMessagesByRoomId = async (roomId = '') => {
    let currentUser = await doGetCurrentUser()
    return currentUser.fetchMultipartMessages({
          roomId: roomId,
          limit: 100,
      }).then(messages => messages)
}
```

Things going on here:
1. default value for param roomId 
1. async/await
1. promise return 



``` js
import { doGetUserMessagesByRoomId } from "../../../chat/chatkit/chatkit";

const fetchMessages = async (roomId) => { 
        setIsLoading(true)
        let messages = await doGetUserMessagesByRoomId(roomId)
        setIsLoading(false)
        return messages
}
```
