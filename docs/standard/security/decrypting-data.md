---
title: "データの復号化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET Framework], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6f2ffaeeb8a92dd7ab16b4ba233196230b595af2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="decrypting-data"></a><span data-ttu-id="453a3-102">データの復号化</span><span class="sxs-lookup"><span data-stu-id="453a3-102">Decrypting Data</span></span>
<span data-ttu-id="453a3-103">復号化は、暗号化の逆の操作です。</span><span class="sxs-lookup"><span data-stu-id="453a3-103">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="453a3-104">秘密キーの暗号化では、データの暗号化に使用されたキーと IV の両方を把握しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="453a3-104">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="453a3-105">公開キーの暗号化では、公開キー (データが秘密キーで暗号化された場合) または秘密キー (データが公開キーで暗号化された場合) のいずれかを把握しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="453a3-105">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>  
  
## <a name="symmetric-decryption"></a><span data-ttu-id="453a3-106">対称復号化</span><span class="sxs-lookup"><span data-stu-id="453a3-106">Symmetric Decryption</span></span>  
 <span data-ttu-id="453a3-107">対称アルゴリズムで暗号化されたデータの復号化は、対称アルゴリズムでデータを暗号化する際に使用するプロセスと似ています。</span><span class="sxs-lookup"><span data-stu-id="453a3-107">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="453a3-108"><xref:System.Security.Cryptography.CryptoStream> クラスは、任意のマネージ ストリーム オブジェクトから読み取られたデータを復号化するために、.NET Framework が提供する対称暗号化クラスと共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="453a3-108">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by the .NET Framework to decrypt data read from any managed stream object.</span></span>  
  
 <span data-ttu-id="453a3-109">次の例は、 <xref:System.Security.Cryptography.RijndaelManaged> クラスのインスタンスを新規作成して、これを <xref:System.Security.Cryptography.CryptoStream> オブジェクトの復号化に使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="453a3-109">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class and use it to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="453a3-110">この例では、まず **RijndaelManaged** クラスのインスタンスを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="453a3-110">This example first creates a new instance of the **RijndaelManaged** class.</span></span> <span data-ttu-id="453a3-111">次に、 **CryptoStream** オブジェクトを作成して、 `MyStream`というマネージ ストリームの値に初期化します。</span><span class="sxs-lookup"><span data-stu-id="453a3-111">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `MyStream`.</span></span> <span data-ttu-id="453a3-112">次に、 **RijndaelManaged** クラスの **CreateDecryptor** メソッドに、暗号化で使用されたキーおよび IV と同じキーと IV が渡されます。これが **CryptoStream** コンストラクターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="453a3-112">Next, the **CreateDecryptor** method from the **RijndaelManaged** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span> <span data-ttu-id="453a3-113">最後に、ストリームに対する読み取りのアクセスを指定するために、 **CryptoStreamMode.Read** 列挙体が **CryptoStream** コンストラクターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="453a3-113">Finally, the **CryptoStreamMode.Read** enumeration is passed to the **CryptoStream** constructor to specify read access to the stream.</span></span>  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateDecryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Read)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);  
```  
  
 <span data-ttu-id="453a3-114">次の例は、ストリームの作成、ストリームの復号化、ストリームからの読み取り、およびストリームを閉じるプロセス全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="453a3-114">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="453a3-115">リッスンしているオブジェクトに接続する際にネットワーク ストリームを初期化する <xref:System.Net.Sockets.TcpListener> オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="453a3-115">A <xref:System.Net.Sockets.TcpListener> object is created that initializes a network stream when a connection to the listening object is made.</span></span> <span data-ttu-id="453a3-116">ネットワーク ストリームは、 **CryptoStream** クラスと **RijndaelManaged** クラスを使用して復号化されます。</span><span class="sxs-lookup"><span data-stu-id="453a3-116">The network stream is then decrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="453a3-117">この例は、キーの値と IV の値が正常に転送されたか、以前に一致していたことを前提としています。</span><span class="sxs-lookup"><span data-stu-id="453a3-117">This example assumes that the key and IV values have been either successfully transferred or previously agreed upon.</span></span> <span data-ttu-id="453a3-118">これらの値の暗号化および転送に必要なコードは示されていません。</span><span class="sxs-lookup"><span data-stu-id="453a3-118">It does not show the code needed to encrypt and transfer these values.</span></span>  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Threading  
Imports System.IO  
Imports System.Net  
Imports System.Security.Cryptography  
  
Module Module1  
    Sub Main()  
            'The key and IV must be the same values that were used  
            'to encrypt the stream.    
            Dim Key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim IV As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
        Try  
            'Initialize a TCPListener on port 11000  
            'using the current IP address.  
            Dim TCPListen As New TcpListener(IPAddress.Any, 11000)  
  
            'Start the listener.  
            TCPListen.Start()  
  
            'Check for a connection every five seconds.  
            While Not TCPListen.Pending()  
                Console.WriteLine("Still listening. Will try in 5 seconds.")  
  
                Thread.Sleep(5000)  
            End While  
  
            'Accept the client if one is found.  
            Dim TCP As TcpClient = TCPListen.AcceptTcpClient()  
  
            'Create a network stream from the connection.  
            Dim NetStream As NetworkStream = TCP.GetStream()  
  
            'Create a new instance of the RijndaelManaged class  
            'and decrypt the stream.  
            Dim RMCrypto As New RijndaelManaged()  
  
            'Create an instance of the CryptoStream class, pass it the NetworkStream, and decrypt   
            'it with the Rijndael class using the key and IV.  
            Dim CryptStream As New CryptoStream(NetStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read)  
  
            'Read the stream.  
            Dim SReader As New StreamReader(CryptStream)  
  
            'Display the message.  
            Console.WriteLine("The decrypted original message: {0}", SReader.ReadToEnd())  
  
            'Close the streams.  
            SReader.Close()  
            NetStream.Close()  
            TCP.Close()  
            'Catch any exceptions.   
        Catch  
            Console.WriteLine("The Listener Failed.")  
        End Try  
    End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Threading;  
using System.IO;  
using System.Net;  
using System.Security.Cryptography;  
  
class Class1  
{  
   static void Main(string[] args)  
   {  
      //The key and IV must be the same values that were used  
      //to encrypt the stream.    
      byte[] Key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      byte[] IV = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      try  
      {  
         //Initialize a TCPListener on port 11000  
         //using the current IP address.  
         TcpListener TCPListen = new TcpListener(IPAdress.Any, 11000);  
  
         //Start the listener.  
         TCPListen.Start();  
  
         //Check for a connection every five seconds.  
         while(!TCPListen.Pending())  
         {  
            Console.WriteLine("Still listening. Will try in 5 seconds.");  
            Thread.Sleep(5000);  
         }  
  
         //Accept the client if one is found.  
         TcpClient TCP = TCPListen.AcceptTcpClient();  
  
         //Create a network stream from the connection.  
         NetworkStream NetStream = TCP.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and decrypt the stream.  
         RijndaelManaged RMCrypto = new RijndaelManaged();  
  
         //Create a CryptoStream, pass it the NetworkStream, and decrypt   
         //it with the Rijndael class using the key and IV.  
         CryptoStream CryptStream = new CryptoStream(NetStream,   
            RMCrypto.CreateDecryptor(Key, IV),   
            CryptoStreamMode.Read);  
  
         //Read the stream.  
         StreamReader SReader = new StreamReader(CryptStream);  
  
         //Display the message.  
         Console.WriteLine("The decrypted original message: {0}", SReader.ReadToEnd());  
  
         //Close the streams.  
         SReader.Close();  
         NetStream.Close();  
         TCP.Close();  
      }  
      //Catch any exceptions.   
      catch  
      {  
         Console.WriteLine("The Listener Failed.");  
      }  
   }  
}  
```  
  
 <span data-ttu-id="453a3-119">前のサンプルを機能させるには、リスナーに対して暗号化された接続を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="453a3-119">For the previous sample to work, an encrypted connection must be made to the listener.</span></span> <span data-ttu-id="453a3-120">接続では、リスナーで使用するキー、IV、およびアルゴリズムと同じものを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="453a3-120">The connection must use the same key, IV, and algorithm used in the listener.</span></span> <span data-ttu-id="453a3-121">このような接続が行われた場合、メッセージが復号化され、コンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="453a3-121">If such a connection is made, the message is decrypted and displayed to the console.</span></span>  
  
## <a name="asymmetric-decryption"></a><span data-ttu-id="453a3-122">非対称復号化</span><span class="sxs-lookup"><span data-stu-id="453a3-122">Asymmetric Decryption</span></span>  
 <span data-ttu-id="453a3-123">通常は、パーティ (パーティ A) は、公開キーと秘密キーの両方を生成し、メモリ内、または暗号化キー コンテナーのいずれかに格納します。</span><span class="sxs-lookup"><span data-stu-id="453a3-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span>  <span data-ttu-id="453a3-124">パーティ A は公開キーを別のパーティ (パーティ B) に送信します。</span><span class="sxs-lookup"><span data-stu-id="453a3-124">Party A then sends the public key to another party (party B).</span></span>  <span data-ttu-id="453a3-125">パーティ B は、公開キーを使用して、データを暗号化してからパーティ A にデータを返信します。パーティ A は、データを受信すると、対応する秘密キーを使用して暗号化を解除します。</span><span class="sxs-lookup"><span data-stu-id="453a3-125">Using the public key, party B encrypts data and sends the data back to party A.  After receiving the data, party A decrypts it using the private key that corresponds.</span></span>  <span data-ttu-id="453a3-126">復号化は、パーティ B がデータの暗号化に使用した公開キーに対応する秘密キーをパーティ A が使用する場合にのみ成功します。</span><span class="sxs-lookup"><span data-stu-id="453a3-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>  
  
 <span data-ttu-id="453a3-127">セキュリティで保護された暗号化キー コンテナーに非対称キーを格納する方法と、その後非対称キーを取得する方法については、「 [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="453a3-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="453a3-128">次の例は、対称キーと IV を表す 2 つのバイト配列の復号化を示しています。</span><span class="sxs-lookup"><span data-stu-id="453a3-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span>  <span data-ttu-id="453a3-129">第三者に簡単に送信できる形式で <xref:System.Security.Cryptography.RSACryptoServiceProvider> オブジェクトから非対称の公開キーを抽出する方法については、「 [Encrypting Data](../../../docs/standard/security/encrypting-data.md)というマネージ ストリームの値に初期化します。</span><span class="sxs-lookup"><span data-stu-id="453a3-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object in a format that you can easily send to a third party, see [Encrypting Data](../../../docs/standard/security/encrypting-data.md).</span></span>  
  
```vb  
'Create a new instance of the RSACryptoServiceProvider class.  
Dim RSA As New RSACryptoServiceProvider()  
  
' Export the public key information and send it to a third party.  
' Wait for the third party to encrypt some data and send it back.  
  
'Decrypt the symmetric key and IV.  
SymmetricKey = RSA.Decrypt(EncryptedSymmetricKey, False)  
SymmetricIV = RSA.Decrypt(EncryptedSymmetricIV, False)  
```  
  
```csharp  
//Create a new instance of the RSACryptoServiceProvider class.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
// Export the public key information and send it to a third party.  
// Wait for the third party to encrypt some data and send it back.  
  
//Decrypt the symmetric key and IV.  
SymmetricKey = RSA.Decrypt( EncryptedSymmetricKey, false);  
SymmetricIV = RSA.Decrypt( EncryptedSymmetricIV , false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="453a3-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="453a3-130">See Also</span></span>  
 [<span data-ttu-id="453a3-131">暗号化と復号化のためのキーの生成</span><span class="sxs-lookup"><span data-stu-id="453a3-131">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [<span data-ttu-id="453a3-132">データの暗号化</span><span class="sxs-lookup"><span data-stu-id="453a3-132">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)  
 [<span data-ttu-id="453a3-133">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="453a3-133">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
