---
title: "データの暗号化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "非対称暗号化"
  - "暗号化 [.NET Framework], 非対称"
  - "暗号化 [.NET Framework], 共通"
  - "対称暗号化"
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# データの暗号化
対称暗号化と非対称暗号化は、異なるプロセスを使用して実行されます。 対称暗号化は、ストリーム上で実行されるため、大量のデータの暗号化に役立ちます。 非対称暗号化は、少ないバイト数で実行されるため、少量のデータにのみ役立ちます。  
  
## 対称暗号化  
 マネージ対称暗号化クラスは、ストリームに読み取られるデータを暗号化する <xref:System.Security.Cryptography.CryptoStream> という特別なストリーム クラスと共に使用されます。**CryptoStream** クラスは、マネージ ストリーム クラスを使用して初期化されます。クラスは、\(暗号化アルゴリズムを実装するクラスから作成された\) <xref:System.Security.Cryptography.ICryptoTransform> インターフェイス、および **CryptoStream** に対して許可されたアクセスの種類について記述した <xref:System.Security.Cryptography.CryptoStreamMode> 列挙体を実装します。**CryptoStream** クラスは、<xref:System.IO.Stream> クラスから派生する任意のクラス \(<xref:System.IO.FileStream>、<xref:System.IO.MemoryStream>、<xref:System.Net.Sockets.NetworkStream> など\) を使用して初期化できます。  これらのクラスを使用すると、さまざまなストリーム オブジェクトの対称暗号化を実行できます。  
  
 次の例は、Rijndael 暗号化アルゴリズムを実装する <xref:System.Security.Cryptography.RijndaelManaged> クラスの新しいインスタンスを作成し、これを使用して **CryptoStream** クラスで暗号化を実行する方法を示しています。 この例では、**CryptoStream**  は `MyStream` と呼ばれるストリーム オブジェクトで初期化されています。これは任意の種類のマネージ ストリームにすることができます。**RijndaelManaged** クラスの **CreateEncryptor** メソッドには、暗号化で使用されるキーと IV が渡されます。 この場合、`RMCrypto` から生成された既定のキーと IV が使用されます。 最後に、ストリームへの書き込みのアクセスを指定する **CryptoStreamMode.Write** が渡されます。  
  
```vb  
Dim RMCrypto As New RijndaelManaged() Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateEncryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Write)  
  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged(); CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 このコードの実行後に **CryptoStream** オブジェクトに書き込まれたデータはすべて、Rijndael アルゴリズムを使用して暗号化されます。  
  
 次の例は、ストリームの作成、ストリームの暗号化、ストリームへの書き込み、およびストリームを閉じるプロセス全体を示しています。 この例では、**CryptoStream** クラスと **RijndaelManaged** クラスを使用して暗号化されたネットワーク ストリームを作成します。<xref:System.IO.StreamWriter> クラスを使用して、暗号化されたストリームにメッセージが書き込まれます。  
  
> [!NOTE]
>  また、この例を使用してファイルに書き込むこともできます。 それを行うには、<xref:System.Net.Sockets.TcpClient> の参照を削除し、<xref:System.Net.Sockets.NetworkStream> を <xref:System.IO.FileStream> に置き換えます。  
  
```vb  
Imports System Imports System.IO Imports System.Security.Cryptography Imports System.Net.Sockets Module Module1 Sub Main() Try 'Create a TCP connection to a listening TCP process. 'Use "localhost" to specify the current computer or 'replace "localhost" with the IP address of the 'listening process. Dim TCP As New TcpClient("localhost", 11000) 'Create a network stream from the TCP connection. Dim NetStream As NetworkStream = TCP.GetStream() 'Create a new instance of the RijndaelManaged class 'and encrypt the stream. Dim RMCrypto As New RijndaelManaged() Dim Key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16} Dim IV As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16} 'Create a CryptoStream, pass it the NetworkStream, and encrypt 'it with the Rijndael class. Dim CryptStream As New CryptoStream(NetStream, RMCrypto.CreateEncryptor(Key, IV), CryptoStreamMode.Write) 'Create a StreamWriter for easy writing to the 'network stream. Dim SWriter As New StreamWriter(CryptStream) 'Write to the stream. SWriter.WriteLine("Hello World!") 'Inform the user that the message was written 'to the stream. Console.WriteLine("The message was sent.") 'Close all the connections. SWriter.Close() CryptStream.Close() NetStream.Close() TCP.Close() Catch 'Inform the user that an exception was raised. Console.WriteLine("The connection failed.") End Try End Sub End Module  
  
```  
  
```csharp  
using System; using System.IO; using System.Security.Cryptography; using System.Net.Sockets; public class main { public static void Main(string[] args) { try { //Create a TCP connection to a listening TCP process. //Use "localhost" to specify the current computer or //replace "localhost" with the IP address of the //listening process. TcpClient TCP = new TcpClient("localhost",11000); //Create a network stream from the TCP connection. NetworkStream NetStream = TCP.GetStream(); //Create a new instance of the RijndaelManaged class // and encrypt the stream. RijndaelManaged RMCrypto = new RijndaelManaged(); byte[] Key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16}; byte[] IV = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16}; //Create a CryptoStream, pass it the NetworkStream, and encrypt //it with the Rijndael class. CryptoStream CryptStream = new CryptoStream(NetStream, RMCrypto.CreateEncryptor(Key, IV), CryptoStreamMode.Write); //Create a StreamWriter for easy writing to the //network stream. StreamWriter SWriter = new StreamWriter(CryptStream); //Write to the stream. SWriter.WriteLine("Hello World!"); //Inform the user that the message was written //to the stream. Console.WriteLine("The message was sent."); //Close all the connections. SWriter.Close(); CryptStream.Close(); NetStream.Close(); TCP.Close(); } catch { //Inform the user that an exception was raised. Console.WriteLine("The connection failed."); } } }  
```  
  
 前の例を正しく実行するためには、<xref:System.Net.Sockets.TcpClient> クラスで指定された IP アドレスとポート番号をリッスンしているプロセスが存在する必要があります。 リッスンしているプロセスが存在する場合は、コードがリッスンしているプロセスに接続して、Rijndael の対称アルゴリズムを使用してストリームを暗号化し、"Hello World\!" を ストリームに書き込みます。 コードが正常に実行された場合、コンソールに次のテキストが表示されます。  
  
```  
The message was sent.  
```  
  
 ただし、リッスンしているプロセスが見つからないか、例外が発生した場合、コードによってコンソールに次のテキストが表示されます。  
  
```  
The connection failed.  
```  
  
## 非対称暗号化  
 非対称アルゴリズムは、通常は対称キーと IV の暗号化など、少量のデータの暗号化に使用されます。 通常、非対称暗号化を行う個人や組織は、別のパーティによって生成された公開キーを使用します。<xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスは、この目的のために、.NET Framework によって提供されます。  
  
 次の例では、公開キーの情報を使用して対称キーと IV を暗号化します。 サード パーティの公開キーを表す 2 つのバイト配列が初期化されます。<xref:System.Security.Cryptography.RSAParameters> オブジェクトがこれらの値に初期化されます。 次に、**RSAParameters** オブジェクトが \(このオブジェクトが表す公開キーと共に\) <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=fullName> メソッドを使用して **RSACryptoServiceProvider** にインポートされます。 最後に、<xref:System.Security.Cryptography.RijndaelManaged> クラスが作成した秘密キーと IV が暗号化されます。 この例では、システムに 128 ビット暗号化がインストールされている必要があります。  
  
```vb  
Imports System Imports System.Security.Cryptography Module Module1 Sub Main() 'Initialize the byte arrays to the public key information. Dim PublicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147} Dim Exponent As Byte() = {1, 0, 1} 'Create values to store encrypted symmetric keys. Dim EncryptedSymmetricKey() As Byte Dim EncryptedSymmetricIV() As Byte 'Create a new instance of the RSACryptoServiceProvider class. Dim RSA As New RSACryptoServiceProvider() 'Create a new instance of the RSAParameters structure. Dim RSAKeyInfo As New RSAParameters() 'Set RSAKeyInfo to the public key values. RSAKeyInfo.Modulus = PublicKey RSAKeyInfo.Exponent = Exponent 'Import key parameters into RSA. RSA.ImportParameters(RSAKeyInfo) 'Create a new instance of the RijndaelManaged class. Dim RM As New RijndaelManaged() 'Encrypt the symmetric key and IV. EncryptedSymmetricKey = RSA.Encrypt(RM.Key, False) EncryptedSymmetricIV = RSA.Encrypt(RM.IV, False) End Sub End Module  
  
```  
  
```csharp  
using System; using System.Security.Cryptography; class Class1 { static void Main() { //Initialize the byte arrays to the public key information. byte[] PublicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56, 74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222, 207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175, 108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194, 240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139, 168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171, 38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93, 106,99,179,68,175,211,164,116,64,148,226,254,172,147}; byte[] Exponent = {1,0,1}; //Create values to store encrypted symmetric keys. byte[] EncryptedSymmetricKey; byte[] EncryptedSymmetricIV; //Create a new instance of the RSACryptoServiceProvider class. RSACryptoServiceProvider RSA = new RSACryptoServiceProvider(); //Create a new instance of the RSAParameters structure. RSAParameters RSAKeyInfo = new RSAParameters(); //Set RSAKeyInfo to the public key values. RSAKeyInfo.Modulus = PublicKey; RSAKeyInfo.Exponent = Exponent; //Import key parameters into RSA. RSA.ImportParameters(RSAKeyInfo); //Create a new instance of the RijndaelManaged class. RijndaelManaged RM = new RijndaelManaged(); //Encrypt the symmetric key and IV. EncryptedSymmetricKey = RSA.Encrypt(RM.Key, false); EncryptedSymmetricIV = RSA.Encrypt(RM.IV, false); } }  
```  
  
## 参照  
 [暗号化と復号化のためのキーの生成](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)   
 [データの復号化](../../../docs/standard/security/decrypting-data.md)   
 [暗号サービス](../../../docs/standard/security/cryptographic-services.md)