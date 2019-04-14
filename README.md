# esnextstuff



Return a reversed copy of it

const invertArray = array => [...array].reverse();



``` js
import ChatMessage from "../../Molecules/ChatMessage/ChatMessage";

export const Conversation = ({ senderId, messages }) => {

    const getMessageParts = ({ parts = [] }) => parts
    const getMessagePayLoad = ({ payload = {} }) => payload
    const getMessageContent = message => getMessageParts(message).map(parts => getMessagePayLoad(parts).content)
    const getMessageContent2 = ({ parts : [{payload : {content}} = {}] = []}) => content
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

