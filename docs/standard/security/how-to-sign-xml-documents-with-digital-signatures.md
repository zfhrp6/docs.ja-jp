---
title: "方法 : デジタル署名で XML ドキュメントに署名する"
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
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSACryptoServiceProvider class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 95f610922126074017802ef53670b26b3596e17c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="85fe0-102">方法 : デジタル署名で XML ドキュメントに署名する</span><span class="sxs-lookup"><span data-stu-id="85fe0-102">How to: Sign XML Documents with Digital Signatures</span></span>
<span data-ttu-id="85fe0-103"><xref:System.Security.Cryptography.Xml> 名前空間のクラスを使用すると、XML ドキュメントまたは XML ドキュメントの一部にデジタル署名で署名することができます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="85fe0-104">XML デジタル署名 (XMLDSIG) を使用すると、データが署名後に変更されなかったことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="85fe0-105">XMLDSIG 標準の詳細については、World Wide Web Consortium (W3C) の推奨事項を参照してください。 [XML 署名の構文と処理](http://go.microsoft.com/fwlink/?LinkID=136777)です。</span><span class="sxs-lookup"><span data-stu-id="85fe0-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](http://go.microsoft.com/fwlink/?LinkID=136777).</span></span>  
  
 <span data-ttu-id="85fe0-106">この手順のコード例は、XML ドキュメント全体にデジタル署名する方法、および <`Signature`> 要素内のドキュメントに署名を付す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="85fe0-106">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="85fe0-107">この例では、RSA 署名キーを作成し、キーをセキュリティで保護されたキー コンテナーに追加してから、キーを使用して XML ドキュメントにデジタル署名しています。</span><span class="sxs-lookup"><span data-stu-id="85fe0-107">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="85fe0-108">キーは、XML デジタル署名を確認するために取得したり、別の XML ドキュメントの署名に使用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-108">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
 <span data-ttu-id="85fe0-109">この手順を使用して作成された XML デジタル署名を検証する方法については、次を参照してください。[する方法: XML ドキュメントのデジタル署名のことを確認](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)です。</span><span class="sxs-lookup"><span data-stu-id="85fe0-109">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="85fe0-110">XML ドキュメントにデジタル署名するには</span><span class="sxs-lookup"><span data-stu-id="85fe0-110">To digitally sign an XML document</span></span>  
  
1.  <span data-ttu-id="85fe0-111"><xref:System.Security.Cryptography.CspParameters> オブジェクトを作成し、キーのコンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="85fe0-112"><xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスを使用して非対称キーを生成します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-112">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="85fe0-113"><xref:System.Security.Cryptography.CspParameters> オブジェクトを <xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスのコンストラクターに渡すと、キーは自動的にキー コンテナーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-113">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="85fe0-114">このキーは、XML ドキュメントの署名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-114">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="85fe0-115">ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="85fe0-116"><xref:System.Xml.XmlDocument> オブジェクトには、暗号化する XML 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="85fe0-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="85fe0-117"><xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトを新規作成し、それに <xref:System.Xml.XmlDocument> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-117">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="85fe0-118">署名する RSA キーを <xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-118">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="85fe0-119">署名内容について記述する <xref:System.Security.Cryptography.Xml.Reference> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-119">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="85fe0-120">ドキュメント全体に署名するには、<xref:System.Security.Cryptography.Xml.Reference.Uri%2A> プロパティを `""` に設定します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-120">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="85fe0-121"><xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> オブジェクトを <xref:System.Security.Cryptography.Xml.Reference> オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-121">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="85fe0-122">変換を使用すると、検証側は、署名側が使用した方法と同一の方法で XML データを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-122">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="85fe0-123">XML データはさまざまな方法で表すことができるため、この手順は検証にとって重要です。</span><span class="sxs-lookup"><span data-stu-id="85fe0-123">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8.  <span data-ttu-id="85fe0-124"><xref:System.Security.Cryptography.Xml.Reference> オブジェクトを <xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-124">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="85fe0-125"><xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> メソッドを呼び出して署名を計算します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-125">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="85fe0-126">署名の XML 表記 (<`Signature`> 要素) を取得して、新しい <xref:System.Xml.XmlElement> オブジェクトに保存します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-126">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="85fe0-127"><xref:System.Xml.XmlDocument> オブジェクトに要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-127">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="85fe0-128">ドキュメントを保存します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-128">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="85fe0-129">例</span><span class="sxs-lookup"><span data-stu-id="85fe0-129">Example</span></span>  
 <span data-ttu-id="85fe0-130">この例では、`test.xml` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="85fe0-130">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="85fe0-131">次の XML を `test.xml` というファイルに配置し、この例で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-131">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToSignXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToSignXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="85fe0-132">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="85fe0-132">Compiling the Code</span></span>  
  
-   <span data-ttu-id="85fe0-133">この例をコンパイルするには、`System.Security.dll` への参照を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="85fe0-133">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="85fe0-134">名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-134">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="85fe0-135">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="85fe0-135">.NET Framework Security</span></span>  
 <span data-ttu-id="85fe0-136">非対称キー ペアの秘密キーをプレーンテキストで保存または転送しないでください。</span><span class="sxs-lookup"><span data-stu-id="85fe0-136">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="85fe0-137">対称キーと非対称暗号化キーの詳細については、次を参照してください。[暗号化と復号化キーの生成](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)です。</span><span class="sxs-lookup"><span data-stu-id="85fe0-137">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="85fe0-138">秘密キーをソース コードに直接埋め込まないでください。</span><span class="sxs-lookup"><span data-stu-id="85fe0-138">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="85fe0-139">使用してアセンブリから、埋め込まれたキーを簡単に読み取ることができます、 [Ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)またはメモ帳などのテキスト エディターで、アセンブリを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-139">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85fe0-140">参照</span><span class="sxs-lookup"><span data-stu-id="85fe0-140">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="85fe0-141">方法: XML ドキュメントのデジタル署名を検証する</span><span class="sxs-lookup"><span data-stu-id="85fe0-141">How to: Verify the Digital Signatures of XML Documents</span></span>](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)
