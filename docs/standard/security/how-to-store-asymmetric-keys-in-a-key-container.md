---
title: "方法 : キー コンテナーに非対称キーを格納する"
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
- cryptography [.NET Framework], asymmetric keys
- storing asymmetric keys
- keys, asymmetric
- encryption keys
- keys, storing in key containers
- asymmetric keys [.NET Framework]
- encryption [.NET Framework], asymmetric keys
- decryption keys
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 475139230c4b58bc6dcc307bd99eeafdc3e89e53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a><span data-ttu-id="496a4-102">方法 : キー コンテナーに非対称キーを格納する</span><span class="sxs-lookup"><span data-stu-id="496a4-102">How to: Store Asymmetric Keys in a Key Container</span></span>
<span data-ttu-id="496a4-103">非対称秘密キーは、ローカル コンピューターにそのまま平文として保存しないでください。</span><span class="sxs-lookup"><span data-stu-id="496a4-103">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="496a4-104">秘密キーを格納する必要がある場合は、キー コンテナーを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="496a4-104">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="496a4-105">キー コンテナーの詳細については、「[コンピューター レベルおよびユーザー レベルの RSA キー コンテナーについて](http://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="496a4-105">For more information on key containers, see [Understanding Machine-Level and User-Level RSA Key Containers](http://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9).</span></span>  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a><span data-ttu-id="496a4-106">非対称キーを作成し、キー コンテナーに格納するには</span><span class="sxs-lookup"><span data-stu-id="496a4-106">To create an asymmetric key and save it in a key container</span></span>  
  
1.  <span data-ttu-id="496a4-107">新しいインスタンスを作成、<xref:System.Security.Cryptography.CspParameters>クラスし、キー コンテナーを呼び出したい名前を渡す、<xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType>フィールドです。</span><span class="sxs-lookup"><span data-stu-id="496a4-107">Create a new instance of a <xref:System.Security.Cryptography.CspParameters> class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>  
  
2.  <span data-ttu-id="496a4-108">派生したクラスの新しいインスタンスを作成、<xref:System.Security.Cryptography.AsymmetricAlgorithm>クラス (通常**RSACryptoServiceProvider**または**DSACryptoServiceProvider**) を渡す前に作成した**CspParameters**オブジェクト コンス トラクターをします。</span><span class="sxs-lookup"><span data-stu-id="496a4-108">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually **RSACryptoServiceProvider** or **DSACryptoServiceProvider**) and pass the previously created **CspParameters** object to its constructor.</span></span>  
  
### <a name="to-delete-the-key-from-a-key-container"></a><span data-ttu-id="496a4-109">キー コンテナーからキーを削除するには</span><span class="sxs-lookup"><span data-stu-id="496a4-109">To delete the key from a key container</span></span>  
  
1.  <span data-ttu-id="496a4-110">**CspParameters** クラスの新しいインスタンスを作成し、キー コンテナーを呼び出すときに使用する名前を **CspParameters.KeyContainerName** フィールドに渡します。</span><span class="sxs-lookup"><span data-stu-id="496a4-110">Create a new instance of a **CspParameters** class and pass the name that you want to call the key container to the **CspParameters.KeyContainerName** field.</span></span>  
  
2.  <span data-ttu-id="496a4-111">**AsymmetricAlgorithm** クラスから派生したクラス (通常は **RSACryptoServiceProvider** または **DSACryptoServiceProvider**) の新しいインスタンスを作成し、前に作成した **CspParameters** オブジェクトをそのコンストラクターに渡します。</span><span class="sxs-lookup"><span data-stu-id="496a4-111">Create a new instance of a class that derives from the **AsymmetricAlgorithm** class (usually **RSACryptoServiceProvider** or **DSACryptoServiceProvider**) and pass the previously created **CspParameters** object to its constructor.</span></span>  
  
3.  <span data-ttu-id="496a4-112">**AsymmetricAlgorithm** から派生したクラスの **PersistKeyInCSP** プロパティを **false** (Visual Basic では **False**) に設定します。</span><span class="sxs-lookup"><span data-stu-id="496a4-112">Set the **PersistKeyInCSP** property of the class that derives from **AsymmetricAlgorithm** to **false** (**False** in Visual Basic).</span></span>  
  
4.  <span data-ttu-id="496a4-113">**AsymmetricAlgorithm** から派生したクラスの **Clear** メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="496a4-113">Call the **Clear** method of the class that derives from **AsymmetricAlgorithm**.</span></span> <span data-ttu-id="496a4-114">このメソッドは、クラスのすべてのリソースを解放し、キー コンテナーを消去します。 </span><span class="sxs-lookup"><span data-stu-id="496a4-114">This method releases all resources of the class and clears the key container.</span></span>  
  
## <a name="example"></a><span data-ttu-id="496a4-115">例</span><span class="sxs-lookup"><span data-stu-id="496a4-115">Example</span></span>  
 <span data-ttu-id="496a4-116">非対称キーを作成し、それをキー コンテナーへ格納し、後でキーを取得し、最後にキー コンテナーからキーを削除する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="496a4-116">The following example demonstrates how to create an asymmetric key, save it in a key container, retrieve the key at a later time, and delete the key from the container.</span></span>  
  
 <span data-ttu-id="496a4-117">`GenKey_SaveInContainer` メソッドと `GetKeyFromContainer` メソッドのコードは類似していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="496a4-117">Notice that code in the `GenKey_SaveInContainer` method and the `GetKeyFromContainer` method is similar.</span></span>  <span data-ttu-id="496a4-118"><xref:System.Security.Cryptography.CspParameters> オブジェクトのキー コンテナー名を指定した場合、<xref:System.Security.Cryptography.AsymmetricAlgorithm> プロパティまたは <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> プロパティを true に設定して、指定したキー コンテナーを <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> オブジェクトに渡すと、次のような処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="496a4-118">When you specify a key container name for a <xref:System.Security.Cryptography.CspParameters> object and pass it to an <xref:System.Security.Cryptography.AsymmetricAlgorithm> object with the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> property or <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> property set to true, the following occurs.</span></span>  <span data-ttu-id="496a4-119">指定した名前のキー コンテナーが存在しない場合、コンテナーが作成されてキーが保持されます。</span><span class="sxs-lookup"><span data-stu-id="496a4-119">If a key container with the specified name does not exist, then one is created and the key is persisted.</span></span>  <span data-ttu-id="496a4-120">指定した名前のキー コンテナーが存在する場合、そのコンテナー内のキーが現在の <xref:System.Security.Cryptography.AsymmetricAlgorithm> オブジェクトに自動的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="496a4-120">If a key container with the specified name does exist, then the key in the container is automatically loaded into the current <xref:System.Security.Cryptography.AsymmetricAlgorithm> object.</span></span>  <span data-ttu-id="496a4-121">つまり、最初に実行される `GenKey_SaveInContainer` メソッドのコードはこのキーを保持し、2 番目に実行される `GetKeyFromContainer` メソッドのコードはこのキーを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="496a4-121">Therefore, the code in the `GenKey_SaveInContainer` method persists the key because it is run first, while the code in the `GetKeyFromContainer` method loads the key because it is run second.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
 _  
  
Public Class StoreKey  
  
    Public Shared Sub Main()  
        Try  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
        Catch e As CryptographicException  
            Console.WriteLine(e.Message)  
        End Try  
    End Sub  
  
    Public Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        ' name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key added to container:  {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub GetKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Delete the key entry in the container.  
        rsa.PersistKeyInCsp = False  
  
        ' Call Clear to release resources and delete the key from the container.  
        rsa.Clear()  
  
        Console.WriteLine("Key deleted.")  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
  
public class StoreKey  
  
{  
    public static void Main()  
    {  
        try  
        {  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
        }  
        catch(CryptographicException e)  
        {  
            Console.WriteLine(e.Message);  
        }  
  
    }  
  
    public static void GenKey_SaveInContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key added to container: \n  {0}", rsa.ToXmlString(true));  
    }  
  
    public static void GetKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : \n {0}", rsa.ToXmlString(true));  
    }  
  
    public static void DeleteKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Delete the key entry in the container.  
        rsa.PersistKeyInCsp = false;  
  
        // Call Clear to release resources and delete the key from the container.  
        rsa.Clear();  
  
        Console.WriteLine("Key deleted.");  
    }  
}  
```  
  
```Output  
Key added to container:  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key retrieved from container :  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key deleted.  
Key added to container:  
<RSAKeyValue> Key Information B</RSAKeyValue>  
Key deleted.  
```  
  
## <a name="see-also"></a><span data-ttu-id="496a4-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="496a4-122">See Also</span></span>  
 [<span data-ttu-id="496a4-123">暗号化と復号化のためのキーの生成</span><span class="sxs-lookup"><span data-stu-id="496a4-123">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [<span data-ttu-id="496a4-124">データの暗号化</span><span class="sxs-lookup"><span data-stu-id="496a4-124">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)  
 [<span data-ttu-id="496a4-125">データの復号化</span><span class="sxs-lookup"><span data-stu-id="496a4-125">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)  
 [<span data-ttu-id="496a4-126">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="496a4-126">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
