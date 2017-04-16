---
title: "方法 : X.509 証明書で XML 要素を復号化する | Microsoft Docs"
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
  - "証明書, X.509 証明書"
  - "復号化"
  - "System.Security.Cryptography.EncryptedXml クラス"
  - "System.Security.Cryptography.X509Certificate2 クラス"
  - "X.509 証明書"
  - "XML の暗号化"
ms.assetid: bd015722-d88d-408d-8ca8-e4e475c441ed
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : X.509 証明書で XML 要素を復号化する
<xref:System.Security.Cryptography.Xml> 名前空間のクラスを使用して、XML ドキュメント内の要素を暗号化および復号化することができます。  XML 暗号化は、データが簡単に読み取られる心配なく、暗号化された XML データを交換または保存する標準的な方法です。  XML 暗号化の規格の詳細については、http:\/\/www.w3.org\/TR\/xmldsig\-core\/ にある World Wide Web Consortium \(W3C\) の XML 暗号化の仕様を参照してください。  
  
 この例では、「[方法 : X.509 証明書で XML 要素を暗号化する](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)」に記載する方法を使用して暗号化された XML 要素を復号化しています。  \<`EncryptedData`\> 要素を検出し、要素を復号化してから、要素を元のプレーン テキストの XML 要素に置き換えます。  
  
 この手順のコード例では、現在のユーザー アカウントのローカルの証明書ストアから X.509 証明書を使用して XML 要素を復号化しています。  この例では、<xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> メソッドを使用して、自動的に X.509 証明書を取得します。また、\<`EncryptedData`\> 要素の \<`EncryptedKey`\> 要素に格納されたセッション キーを復号化します。  次に、<xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> メソッドは、自動的にセッション キーを使用して XML 要素を復号化します。  
  
 この例は、複数のアプリケーションが暗号化されたデータを共有する必要がある状況、または 1 つのアプリケーションが、実行する時間の間に暗号化されたデータを保存する必要がある状況に適しています。  
  
### X.509 キーで XML 要素を復号化するには  
  
1.  ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。  <xref:System.Xml.XmlDocument> オブジェクトには、復号化する XML 要素が含まれています。  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2.  <xref:System.Xml.XmlDocument> オブジェクトをコンストラクターに渡して <xref:System.Security.Cryptography.Xml.EncryptedXml> オブジェクトを新規作成します。  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3.  <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> メソッドを使用して XML ドキュメントを復号化します。  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4.  <xref:System.Xml.XmlDocument> オブジェクトを保存します。  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## 使用例  
 この例では、`"test.xml"` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。  また、`"test.xml"` には `"creditcard"` 要素が含まれることも前提としています。  次の XML を `test.xml` というファイルに配置し、この例で使用することができます。  
  
```  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
  
```  
  
 [!code-csharp[HowToDecryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#1)]  
  
## コードのコンパイル  
  
-   この例をコンパイルするには、`System.Security.dll` への参照を含める必要があります。  
  
-   名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。  
  
## .NET Framework セキュリティ  
 この例で使用される X.509 証明書は、テスト専用です。  アプリケーションは、信頼された証明機関が生成する X.509 証明書、または Microsoft Windows 証明書サーバーによって生成された証明書を使用する必要があります。  
  
## 参照  
 <xref:System.Security.Cryptography.Xml>   
 [方法 : X.509 証明書で XML 要素を暗号化する](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)