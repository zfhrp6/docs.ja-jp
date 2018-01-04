---
title: "暗号化と復号化のためのキーの生成"
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
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 333e99997bad3852ae34753165aa736ef32ac004
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="37be4-102">暗号化と復号化のためのキーの生成</span><span class="sxs-lookup"><span data-stu-id="37be4-102">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="37be4-103">キーの作成と管理は、暗号プロセスの重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="37be4-103">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="37be4-104">対称アルゴリズムでは、キーと初期化ベクター (IV) を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37be4-104">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="37be4-105">キーは、データの暗号化解除を許可しないユーザーに対しては秘密にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="37be4-105">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="37be4-106">IV は秘密にする必要はありませんが、セッションごとに変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37be4-106">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="37be4-107">非対称アルゴリズムでは、公開キーと秘密キーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37be4-107">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="37be4-108">公開キーはだれに公開してもかまいせんが、秘密キーを知らせる相手は、公開キーで暗号化されたデータを復号化する人だけにします。</span><span class="sxs-lookup"><span data-stu-id="37be4-108">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="37be4-109">このセクションでは、対称アルゴリズムと非対称アルゴリズムの両方について、キーを作成して管理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="37be4-109">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="37be4-110">共通キー</span><span class="sxs-lookup"><span data-stu-id="37be4-110">Symmetric Keys</span></span>  
 <span data-ttu-id="37be4-111">.NET Framework に用意されている対称暗号化クラスでは、データを暗号化および復号化するために、キーと新しい初期化ベクター (IV) が必要になります。</span><span class="sxs-lookup"><span data-stu-id="37be4-111">The symmetric encryption classes supplied by the .NET Framework require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="37be4-112">いずれかのマネージ対称暗号化クラスの新しいインスタンスを作成するとき、既定のコンストラクターを使用すると、常に新しいキーと IV が自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="37be4-112">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the default constructor, a new key and IV are automatically created.</span></span> <span data-ttu-id="37be4-113">自分のデータを復号化できるようにする相手は、自分と同じキーおよび IV を所有し、同じアルゴリズムを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37be4-113">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="37be4-114">一般に、キーと IV はセッションごとに新しく作成する必要があり、キーも IV も格納して後のセッションで使用することは望ましくありません。</span><span class="sxs-lookup"><span data-stu-id="37be4-114">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="37be4-115">通常、共通キーと IV を離れた場所にいる人へ送信するためには、非対称暗号化方式を使用して共通キーを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="37be4-115">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="37be4-116">これらの値を暗号化せずに安全でないネットワーク経由で送信することは、値を傍受した人ならだれでもデータを暗号化解除できるようになるため危険です。</span><span class="sxs-lookup"><span data-stu-id="37be4-116">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span> <span data-ttu-id="37be4-117">暗号化を使用したデータ交換の詳細については、「 [暗号スキームの作成](../../../docs/standard/security/creating-a-cryptographic-scheme.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37be4-117">For more information about exchanging data by using encryption, see [Creating a Cryptographic Scheme](../../../docs/standard/security/creating-a-cryptographic-scheme.md).</span></span>  
  
 <span data-ttu-id="37be4-118">TripleDES アルゴリズムを実装する <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> クラスの新しいインスタンスの作成方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="37be4-118">The following example shows the creation of a new instance of the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class that implements the TripleDES algorithm.</span></span>  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
```  
  
 <span data-ttu-id="37be4-119">上記のコードを実行すると新しいキーと IV が生成され、それぞれ **Key** プロパティと **IV** プロパティに設定されます。</span><span class="sxs-lookup"><span data-stu-id="37be4-119">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="37be4-120">複数のキーを生成する必要が生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="37be4-120">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="37be4-121">このような状況では、対称アルゴリズムを実装するクラスの新しいインスタンスを作成し、次に **GenerateKey** および **GenerateIV** メソッドを呼び出すことによって新しいキーと IV を作成します。</span><span class="sxs-lookup"><span data-stu-id="37be4-121">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="37be4-122">非対称暗号化クラスの新しいインスタンスの作成後に新しいキーと IV を作成する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="37be4-122">The following code example illustrates how to create new keys and IVs after a new instance of the asymmetric cryptographic class has been made.</span></span>  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
TDES.GenerateIV()  
TDES.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
TDES.GenerateIV();  
TDES.GenerateKey();  
```  
  
 <span data-ttu-id="37be4-123">上記のコードを実行すると、 **TripleDESCryptoServiceProvider** の新しいインスタンスの作成時にキーと IV が生成されます。</span><span class="sxs-lookup"><span data-stu-id="37be4-123">When the previous code is executed, a key and IV are generated when the new instance of **TripleDESCryptoServiceProvider** is made.</span></span> <span data-ttu-id="37be4-124">**GenerateKey** メソッドと **GenerateIV** メソッドを呼び出すと、別のキーと IV が作成されます。</span><span class="sxs-lookup"><span data-stu-id="37be4-124">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="37be4-125">非対称キー</span><span class="sxs-lookup"><span data-stu-id="37be4-125">Asymmetric Keys</span></span>  
 <span data-ttu-id="37be4-126">.NET Framework には、非対称暗号化方式のための <xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスと <xref:System.Security.Cryptography.DSACryptoServiceProvider> クラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="37be4-126">The .NET Framework provides the <xref:System.Security.Cryptography.RSACryptoServiceProvider> and <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes for asymmetric encryption.</span></span> <span data-ttu-id="37be4-127">これらのクラスの既定のコンストラクターを使用して新しいインスタンスを作成すると、公開キーと秘密キーのペアが作成されます。</span><span class="sxs-lookup"><span data-stu-id="37be4-127">These classes create a public/private key pair when you use the default constructor to create a new instance.</span></span> <span data-ttu-id="37be4-128">非対称キーは、複数のセッションで使用できるように格納したり、1 つのセッション専用として生成したりできます。</span><span class="sxs-lookup"><span data-stu-id="37be4-128">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="37be4-129">公開キーは一般に公開できますが、秘密キーは厳密に保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37be4-129">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="37be4-130">非対称アルゴリズム クラスの新しいインスタンスを作成すると、公開キーと秘密キーのペアが常に生成されます。</span><span class="sxs-lookup"><span data-stu-id="37be4-130">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="37be4-131">クラスの新しいインスタンスを作成したら、次の 2 つの方法のどちらかを使ってキー情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="37be4-131">After a new instance of the class is created, the key information can be extracted using one of two methods:</span></span>  
  
-   <span data-ttu-id="37be4-132"><xref:System.Security.Cryptography.RSA.ToXmlString%2A> メソッド。キー情報の XML 表現を返します。</span><span class="sxs-lookup"><span data-stu-id="37be4-132">The <xref:System.Security.Cryptography.RSA.ToXmlString%2A> method, which returns an XML representation of the key information.</span></span>  
  
-   <span data-ttu-id="37be4-133"><xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> メソッド。キー情報を保持する <xref:System.Security.Cryptography.RSAParameters> 構造体を返します。</span><span class="sxs-lookup"><span data-stu-id="37be4-133">The <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span>  
  
 <span data-ttu-id="37be4-134">どちらのメソッドにも、公開キー情報だけを返すのか、または公開キー情報と秘密キー情報の両方を返すのかを示すブール値を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="37be4-134">Both methods accept a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span> <span data-ttu-id="37be4-135">**メソッドを使用すると、** RSACryptoServiceProvider **クラスを初期化して** RSAParameters <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> 構造体の値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="37be4-135">An **RSACryptoServiceProvider** class can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> method.</span></span>  
  
 <span data-ttu-id="37be4-136">非対称秘密キーは、ローカル コンピューターにそのまま平文として保存しないでください。</span><span class="sxs-lookup"><span data-stu-id="37be4-136">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="37be4-137">秘密キーを格納する必要がある場合は、キー コンテナーを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="37be4-137">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="37be4-138">秘密キーをキー コンテナーに格納する方法の詳細については、「 [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37be4-138">For more on how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="37be4-139">次のコード例では、 **RSACryptoServiceProvider** クラスの新しいインスタンスを作成し、公開キーと秘密キーのペアを作成して、公開キー情報を **RSAParameters** 構造体に保存します。</span><span class="sxs-lookup"><span data-stu-id="37be4-139">The following code example creates a new instance of the **RSACryptoServiceProvider** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
```vb  
'Generate a public/private key pair.  
Dim RSA as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim RSAKeyInfo As RSAParameters = RSA.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters RSAKeyInfo = RSA.ExportParameters(false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="37be4-140">参照</span><span class="sxs-lookup"><span data-stu-id="37be4-140">See Also</span></span>  
 [<span data-ttu-id="37be4-141">データの暗号化</span><span class="sxs-lookup"><span data-stu-id="37be4-141">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)  
 [<span data-ttu-id="37be4-142">データの復号化</span><span class="sxs-lookup"><span data-stu-id="37be4-142">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)  
 [<span data-ttu-id="37be4-143">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="37be4-143">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="37be4-144">方法: キー コンテナーに非対称キーを格納する</span><span class="sxs-lookup"><span data-stu-id="37be4-144">How to: Store Asymmetric Keys in a Key Container</span></span>](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)
