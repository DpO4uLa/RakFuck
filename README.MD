<h1 style="text-align: center;">RakFuck - RakSAMP with steriods API</h1>

<h1 style="text-align: center;">BitStream</h1>

**<h3 style="text-align: center;">The BitStream object is automatically garbage collected when it is no longer referenced.</h3>**

| Syntax | Description |
| -------- | --------- |
| ```local bs = BitStream();```  | Creates a new BitStream object |
| ```bs:writeBool(bool value);``` | Writes a boolean value to the BitStream |
| ```bs:writeInt8(int value);```| Writes an 8-bit signed integer to the BitStream |
| ```bs:writeInt16(int value);```| Writes a 16-bit signed integer to the BitStream |
| ```bs:writeInt32(int value);```| Writes a 32-bit signed integer to the BitStream |
| ```bs:writeUInt8(int value);``` | Writes an 8-bit unsigned integer to the BitStream |
| ```bs:writeUInt16(int value);``` | Writes a 16-bit unsigned integer to the BitStream |
| ```bs:writeUInt32(int value);``` | Writes a 32-bit unsigned integer to the BitStream |
| ```bs:writeFloat(float value);``` | Writes a 32-bit floating point number to the BitStream |
| ```bs:writeString(string value);``` | Writes a string to the BitStream |
| ```bs:writeEncoded(string value);``` | Writes a compressed string to the BitStream |
| ```bs:writeBitStream(BitStream bs);``` | Writes a BitStream to the BitStream |
| ```bs:resetWritePointer();``` | Resets the write pointer to the beginning of the BitStream |
| ```bs:resetReadPointer();``` | Resets the read pointer to the beginning of the BitStream |
| ```bs:ignoreBits(int bits);``` | Ignores the specified number of bits in the BitStream |
| ```bs:ignoreBytes(int bytes);``` | Ignores the specified number of bytes in the BitStream |
| ```bs:reset();``` | Resets the BitStream |
| ```local val = bs:readBool();``` | Reads a boolean value from the BitStream |
| ```local val = bs:readInt8();``` | Reads an 8-bit signed integer from the BitStream |
| ```local val = bs:readInt16();``` | Reads a 16-bit signed integer from the BitStream |
| ```local val = bs:readInt32();``` | Reads a 32-bit signed integer from the BitStream |
| ```local val = bs:readUInt8();``` | Reads an 8-bit unsigned integer from the BitStream |
| ```local val = bs:readUInt16();``` | Reads a 16-bit unsigned integer from the BitStream |
| ```local val = bs:readUInt32();``` | Reads a 32-bit unsigned integer from the BitStream |
| ```local val = bs:readFloat();``` | Reads a 32-bit floating point number from the BitStream |
| ```local val = bs:readString(int length);``` | Reads a string of the specified length from the BitStream |
| ```local val = bs:readEncoded(int length);``` | Reads a compressed string of the specified length from the BitStream |
| ```local val = bs:getWriteOffset();``` | Returns the current write offset in the BitStream |
| ```local val = bs:getReadOffset();``` | Returns the current read offset in the BitStream |
| ```local val = bs:getNumberOfBitsUsed();``` | Returns the number of bits used in the BitStream |
| ```local val = bs:getNumberOfBytesUsed();``` | Returns the number of bytes used in the BitStream |
| ```local val = bs:getNumberOfUnreadBits();``` | Returns the number of unread bits in the BitStream |
| ```local val = bs:getNumberOfUnreadBytes();``` | Returns the number of unread bytes in the BitStream |

<h1 style="text-align: center;">Proxy</h1>

**<h3 style="text-align: center;">The Proxy object is doesnt't automatically garbage collected.</h3>**
**<h3 style="text-align: center;">Use only SOCKS5 UDP proxy.</h3>**
| Syntax | Description |
| -------- | --------- |
| ```local prx = Proxy("ip", "port");``` | Creates a new Proxy object |
| ```local rpx = Proxy("ip", "port", "login", "password");``` | Creates a new Proxy object with login and password |
| ```local ip = prx:getProxyIP();``` | Returns the IP address of the Proxy |
| ```local port = prx:getProxyPort();``` | Returns the port of the Proxy |
| ```local publicIp = prx:getPublicProxyIP();``` | Returns the public IP address of the Proxy |

<h2 style="text-align: center;">ProxyPool</h2>

| Syntax | Description |
| -------- | --------- |
| ```addProxyToPool(Proxy prx);``` | Add a proxy object to the pool and start connect to the proxy |
| ```local val = getProxyCount();``` | Returns the number of proxies in the pool that have been processed. |
| ```function onProxyProcess(prx, status, err)``` | Callback function when a proxy is connected. ```Proxy prx``` is the proxy object, ```bool status``` is true if the connection is successful, and ```string err``` is the error message if the connection is failed.

<h2 style="text-align: center;">Bot</h2>

**<h3 style="text-align: center;">The Bot object is doesnt't automatically garbage collected.</h3>**

| Syntax | Description |
| -------- | --------- |
| ```local bot = Bot();``` | Creates a new Bot object |
| ```bot:setProxy(Proxy prx);``` | Sets the Proxy object for the Bot. if you don't want to use a proxy, be sure to call the method with the Proxy("", "") parameter. Be sure to set a proxy for the bot in any case. |
| ```bot:setServerAddr(string ip);``` | Sets the server address for the Bot |
| ```bot:setServerPort(int port);``` | Sets the server port for the Bot |
| ```bot:setServerPassword(string password);``` | Sets the server password for the Bot |
| ```bot:setName(string login);``` | Sets the name for the Bot |
| ```bot:sendConnect();``` | Sends a connect packet to the server |
| ```bot:sendPacket(BitStream bs);``` | Sends a packet to the server |
| ```bot:sendRPC(int id, BitStream bs);``` | Sends an RPC to the server |
| ```bot:isConnected();``` | Returns true if the bot is connected to the server |
| ```bot:getBotLocalId();``` | Returns the local bot ID |
| ```bot:getName();``` | Returns the name of the bot |
| ```bot:getServerAddr();``` | Returns the server address |
| ```bot:getServerPort();``` | Returns the server port |
| ```bot:getServerPassword();``` | Returns the server password |
| ```bot:setFakePing(bool fake, int ping);``` | Sets the fake ping for the bot |
| ```bot:getPing();``` | Returns the ping of the bot |

<h2 style="text-align: center;">Misc functions</h2>

| Syntax | Description |
| -------- | --------- |
| ```print(string text);``` | Prints a string to the console |
| ```setConsoleTitle(string title);``` | Sets the console title |
| ```addEventHandler(string eventName, function handler);``` | Adds an event handler |
| ```exit();``` | Exits the program |
| ```getAllBots();``` | Returns a table with all bots |

<h2 style="text-align: center;">Events</h2>

| Called when the script is loaded |
| -------- |
```lua
function onLoad()

end
```

| Called when the script is unloaded | 
| -------- |
```lua
function onUnload()

end
```

| Called every 5ms |
| -------- |
```lua
function onUpdate()

end
```

| Called when the bot receives an incoming RPC |
| -------- |
```lua
function onReceiveRPC(botId, rpcId, bs)
    -- botId - local bot ID
    -- rpcId - RPC ID
    -- bs - BitStream object
    return true/false; -- return true to continue, false to stop
end
```

| Called when the bot sends an outgoing RPC |
| -------- |
```lua
function onSendRPC(botId, rpcId, bs)
    -- botId - local bot ID
    -- rpcId - RPC ID
    -- bs - BitStream object
    return true/false; -- return true to continue, false to stop
end
```

| Called when the bot receives an incoming packet |
| -------- |
```lua
function onReceivePacket(botId, bs)
    -- botId - local bot ID
    -- bs - BitStream object
    return true/false; -- return true to continue, false to stop
end
```

| Called when the bot sends an outgoing packet |
| -------- |
```lua
function onSendPacket(botId, bs)
    -- botId - local bot ID
    -- bs - BitStream object
    return true/false; -- return true to continue, false to stop
end
```

| Called when the user types something into the console. |
| -------- |
```lua
function onEnterCommand(arg)
    -- arg - the command entered by the user
end
```

