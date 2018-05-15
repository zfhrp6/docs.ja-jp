---
title: '方法 : 非対称キーで XML 要素を暗号化する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys [.NET Framework]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- Rijndael
- encryption [.NET Framework], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6840a9005aaca4805252298e1ceaf7e51f38971
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="f7fa2-102">方法 : 非対称キーで XML 要素を暗号化する</span><span class="sxs-lookup"><span data-stu-id="f7fa2-102">How to: Encrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="f7fa2-103"><xref:System.Security.Cryptography.Xml> 名前空間のクラスを使用して、XML ドキュメント内の要素を暗号化することができます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="f7fa2-104">XML 暗号化は、データが簡単に読み取られる心配なく、暗号化された XML データを交換または保存する標準的な方法です。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="f7fa2-105">標準の XML 暗号化の詳細については、仕様を参照して、World Wide Web Consortium (W3C) XML の暗号化にあるに対してhttp://www.w3.org/TR/xmldsig-core/です。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="f7fa2-106">XML の暗号化を使用すると、任意の XML 要素またはドキュメントを、暗号化された XML データを含む <`EncryptedData`> 要素があるドキュメントに置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span>  <span data-ttu-id="f7fa2-107">また、<`EncryptedData`> 要素には、暗号化時に使用されたキーとプロセスに関する情報が含まれているサブ要素を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-107">The <`EncryptedData`> element can also contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="f7fa2-108">XML 暗号化を使用すると、ドキュメントに複数の暗号化された要素を含められるだけでなく、要素を複数回暗号化することができます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="f7fa2-109">この手順のコード例は、<`EncryptedData`> 要素および後の復号化時に使用するいくつかの他のサブ要素の作成方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-109">The code example in this procedure shows how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="f7fa2-110">この例では、2 つのキーを使用して XML 要素を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="f7fa2-111">RSA の公開キーと秘密キーのペアを生成し、キーのペアをセキュリティで保護されたキー コンテナーに保存します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-111">It generates an RSA public/private key pair and saves the key pair to a secure key container.</span></span>  <span data-ttu-id="f7fa2-112">この例では、Rijndael アルゴリズムとも呼ばれる Advanced Encryption Standard (AES) アルゴリズムを使用して、別のセッション キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-112">The example then creates a separate session key using the Advanced Encryption Standard (AES) algorithm, also called the Rijndael algorithm.</span></span>  <span data-ttu-id="f7fa2-113">この例では、XML ドキュメントの暗号化に AES セッション キーを使用してから、AES セッション キーを暗号化するために RSA 公開キーを使用しています。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-113">The example uses the AES session key to encrypt the XML document and then uses the RSA public key to encrypt the AES session key.</span></span>  <span data-ttu-id="f7fa2-114">最後に、この例では、暗号化された AES セッション キーと暗号化された XML データを、新しい <`EncryptedData`> 要素内の XML ドキュメントに保存します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-114">Finally, the example saves the encrypted AES session key and the encrypted XML data to the XML document within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="f7fa2-115">XML 要素を復号化するには、キー コンテナーから RSA 秘密キーを取得し、これを使用してセッション キーを復号化してから、セッション キーを使用してドキュメントを復号化します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-115">To decrypt the XML element, you retrieve the RSA private key from the key container, use it to decrypt the session key, and then use the session key to decrypt the document.</span></span>  <span data-ttu-id="f7fa2-116">この手順を使用して暗号化された XML 要素を復号化する方法の詳細については、次を参照してください。[する方法: 非対称キーで XML 要素を復号化](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 <span data-ttu-id="f7fa2-117">この例は、複数のアプリケーションが暗号化されたデータを共有する必要がある状況や、1 つのアプリケーションが、実行する時間の間に暗号化されたデータを保存する必要がある状況に適しています。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="f7fa2-118">非対称キーで XML 要素を暗号化するには</span><span class="sxs-lookup"><span data-stu-id="f7fa2-118">To encrypt an XML element with an asymmetric key</span></span>  
  
1.  <span data-ttu-id="f7fa2-119"><xref:System.Security.Cryptography.CspParameters> オブジェクトを作成し、キーのコンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-119">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="f7fa2-120"><xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスを使用して対称キーを生成します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-120">Generate a symmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="f7fa2-121"><xref:System.Security.Cryptography.CspParameters> オブジェクトを <xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスのコンストラクターに渡すと、キーは自動的にキー コンテナーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-121">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="f7fa2-122">このキーは、AES のセッション キーの暗号化に使用され、後で復号化するために取得することができます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-122">This key will be used to encrypt the AES session key and can be retrieved later to decrypt it.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="f7fa2-123">ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-123">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="f7fa2-124"><xref:System.Xml.XmlDocument> オブジェクトには、暗号化する XML 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-124">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="f7fa2-125"><xref:System.Xml.XmlDocument> オブジェクトで指定された要素を検索し、暗号化する要素を表す新しい <xref:System.Xml.XmlElement> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-125">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span> <span data-ttu-id="f7fa2-126">この例では、`"creditcard"` 要素が暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-126">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="f7fa2-127"><xref:System.Security.Cryptography.RijndaelManaged> クラスを使用してセッション キーを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-127">Create a new session key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="f7fa2-128">このキーは、XML 要素を暗号化してから、このキー自体が暗号化されて XML ドキュメントに配置されます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-128">This key will encrypt the XML element, and then be encrypted itself and placed in the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="f7fa2-129"><xref:System.Security.Cryptography.Xml.EncryptedXml> クラスのインスタンスを新規作成し、これを使用して、セッション キーによって指定された要素を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-129">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the session key.</span></span>  <span data-ttu-id="f7fa2-130"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> メソッドは、暗号化された要素を、暗号化されたバイトの配列として返します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-130">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="f7fa2-131"><xref:System.Security.Cryptography.Xml.EncryptedData> オブジェクトを構築し、暗号化された XML 要素の URL 識別子をそれに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-131">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the encrypted XML element.</span></span>  <span data-ttu-id="f7fa2-132">この URL 識別子は、復号化側に、XML に暗号化された要素が含まれていることを知らせます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-132">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="f7fa2-133">[<xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl>] フィールドを使用すると、URL 識別子を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-133">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  <span data-ttu-id="f7fa2-134">プレーン テキストの XML 要素は、この <xref:System.Security.Cryptography.Xml.EncryptedData> オブジェクトによってカプセル化された <`EncryptedData`> 要素に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-134">The plaintext XML element will be replaced by an <`EncryptedData`> element encapsulated by this <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8.  <span data-ttu-id="f7fa2-135">セッション キーの生成に使用する暗号化アルゴリズムの URL 識別子に初期化された <xref:System.Security.Cryptography.Xml.EncryptionMethod> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-135">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the session key.</span></span>  <span data-ttu-id="f7fa2-136"><xref:System.Security.Cryptography.Xml.EncryptionMethod> オブジェクトを <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> プロパティに渡します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-136">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. <span data-ttu-id="f7fa2-137">暗号化されたセッション キーを格納する <xref:System.Security.Cryptography.Xml.EncryptedKey> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-137">Create an <xref:System.Security.Cryptography.Xml.EncryptedKey> object to contain the encrypted session key.</span></span>  <span data-ttu-id="f7fa2-138">セッション キーを暗号化し、<xref:System.Security.Cryptography.Xml.EncryptedKey> オブジェクトに追加して、セッション キーの名前とキーの識別子の URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-138">Encrypt the session key, add it to the <xref:System.Security.Cryptography.Xml.EncryptedKey> object, and enter a session key name and key identifier URL.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. <span data-ttu-id="f7fa2-139">暗号化されたデータを特定のセッション キーにマップする <xref:System.Security.Cryptography.Xml.DataReference> オブジェクトを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-139">Create a new <xref:System.Security.Cryptography.Xml.DataReference> object that maps the encrypted data to a particular session key.</span></span>  <span data-ttu-id="f7fa2-140">(省略可能) この手順を使用すると、XML ドキュメントの複数の部分が 1 つのキーによって暗号化されたことを簡単に指定できます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-140">This optional step allows you to easily specify that multiple parts of an XML document were encrypted by a single key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. <span data-ttu-id="f7fa2-141">暗号化されたキーを <xref:System.Security.Cryptography.Xml.EncryptedData> オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-141">Add the encrypted key to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. <span data-ttu-id="f7fa2-142">RSA キーの名前を指定する <xref:System.Security.Cryptography.Xml.KeyInfo> オブジェクトを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-142">Create a new <xref:System.Security.Cryptography.Xml.KeyInfo> object to specify the name of the RSA key.</span></span>  <span data-ttu-id="f7fa2-143">このオブジェクトを <xref:System.Security.Cryptography.Xml.EncryptedData> オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-143">Add it to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span> <span data-ttu-id="f7fa2-144">これにより、復号化側は、適切な非対称キーを識別して、セッション キーを復号化する際に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-144">This helps the decrypting party identify the correct asymmetric key to use when decrypting the session key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. <span data-ttu-id="f7fa2-145">暗号化された要素のデータを <xref:System.Security.Cryptography.Xml.EncryptedData> オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-145">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. <span data-ttu-id="f7fa2-146">元の <xref:System.Xml.XmlDocument> オブジェクトの要素を <xref:System.Security.Cryptography.Xml.EncryptedData> 要素に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-146">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. <span data-ttu-id="f7fa2-147"><xref:System.Xml.XmlDocument> オブジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-147">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="f7fa2-148">例</span><span class="sxs-lookup"><span data-stu-id="f7fa2-148">Example</span></span>  
 <span data-ttu-id="f7fa2-149">この例では、`"test.xml"` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-149">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="f7fa2-150">また、`"test.xml"` には `"creditcard"` 要素が含まれることも前提としています。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-150">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="f7fa2-151">次の XML を `test.xml` というファイルに配置し、この例で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-151">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f7fa2-152">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="f7fa2-152">Compiling the Code</span></span>  
  
-   <span data-ttu-id="f7fa2-153">この例をコンパイルするには、`System.Security.dll` への参照を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-153">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="f7fa2-154">名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-154">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f7fa2-155">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f7fa2-155">.NET Framework Security</span></span>  
 <span data-ttu-id="f7fa2-156">対称暗号化キーをプレーンテキストで保存したり、対称キーをコンピューター間でプレーンテキストで転送したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-156">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="f7fa2-157">加えて、非対称キー ペアの秘密キーをプレーンテキストで保存または転送しないでください。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-157">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="f7fa2-158">対称キーと非対称暗号化キーの詳細については、次を参照してください。[暗号化と復号化キーの生成](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-158">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="f7fa2-159">キーをソース コードに直接埋め込まないでください。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-159">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="f7fa2-160">使用してアセンブリから、埋め込まれたキーを簡単に読み取ることができます、 [Ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)またはメモ帳などのテキスト エディターで、アセンブリを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-160">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="f7fa2-161">暗号化キーを使用して完了したら、各バイトをゼロ (0) にするか、マネージ暗号化クラスの <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> メソッドを呼び出してメモリから消去します。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-161">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="f7fa2-162">暗号化キーは、デバッガーによってメモリから読み取られるか、メモリの位置がディスクにページングされている場合はハード ドライブから読み取られることがあります。</span><span class="sxs-lookup"><span data-stu-id="f7fa2-162">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7fa2-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7fa2-163">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="f7fa2-164">方法: 非対称キーで XML 要素を復号化する</span><span class="sxs-lookup"><span data-stu-id="f7fa2-164">How to: Decrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)
