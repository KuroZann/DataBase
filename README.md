# DataBase
📂 Database bot by [kurozann](https://t.me/kurozann)

## ```Fetch to```
```
https://raw.githubusercontent.com/KuroZann/DataBase/main/command
```
## ```Module```
node-fetch or axios

## ```Example on the WhatsApp bot```
```
let handler = async (m, { conn, args, usedPrefix, command }) => {
  conn.chatRead(m.chat);
  conn.sendMessage(m.chat, {
    react: {
      text: '🕒',
      key: m.key,
    }
  });

  try {
    let res = await fetch(`https://raw.githubusercontent.com/KuroZann/DataBase/main/${command}/${command.json}`);
    let json = await res.json();
    let anu = json[Math.floor(Math.random() * json.length)];
    
    await conn.sendFile(m.chat, anu, 'video.mp4', `*◦ Result from :* ${command}`, m);
  } catch (error) {
    console.log(error);
    conn.sendMessage(m.chat, 'An error occurred while sending media', m);
  }
};

handler.help = ['command'].map(v => v + ' */none*');
handler.tags = ['tags'];
handler.command =  /^(command)$/i;

module.exports = handler;
```
