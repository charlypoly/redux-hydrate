# redux-hydrate
Hydrate framework for Redux


```typescript


const container = Hydrate.createContainer();

interface Chat {
  id: string;
  message_ids?: string[]
}

container.register<Chat>('Chat', {
  hasMany: ['Messages']
});

// ...

container.reduxMiddleware();


interface ConnectedProps {
  users?: Users[];
  messages?: Message[];
  message_attachments: MessageAttachment[];
}

interface ComponentProps {
  chat: Chat;
}

interface ComponentState {}

type Props = ConnectedProps & ComponentProps;

class Chat extends React.Component<Props, ComponentState> {

  render() {
    return <div></div>;
  }

}

export default Hydrate.connect<Props, {}, ComponentProps>(
  {
    chat: {
      users: { ensure: true },
      messages: {
        message_attachments: {
          ensure: true
        }
      },
    }
  }
  Chat
);


```
