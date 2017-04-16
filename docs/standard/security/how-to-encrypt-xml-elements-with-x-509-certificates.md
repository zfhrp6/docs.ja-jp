---
title: "方法 : X.509 証明書で XML 要素を暗号化する | Microsoft Docs"
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
  - "暗号化 [.NET Framework], X.509 証明書"
  - "暗号化 [.NET Framework], X.509 証明書"
  - "System.Security.Cryptography.EncryptedXml クラス"
  - "System.Security.Cryptography.X509Certificate2 クラス"
  - "X.509 証明書"
  - "XML の暗号化"
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : X.509 証明書で XML 要素を暗号化する
<xref:System.Security.Cryptography.Xml> 名前空間のクラスを使用して、XML ドキュメント内の要素を暗号化することができます。  XML の暗号化は、データが簡単に読み取られる心配なく、暗号化された XML データを交換または保存する標準的な方法です。  XML 暗号化の基準の詳細については、http:\/\/www.w3.org\/TR\/xmldsig\-core\/ にある World Wide Web Consortium \(W3C\) の XML 暗号化の仕様を参照してください。  
  
 XML の暗号化を使用すると、任意の XML 要素またはドキュメントを、暗号化された XML データを含む \<`EncryptedData`\> 要素があるドキュメントに置き換えることができます。  \<`EncryptedData`\> 要素には、暗号化時に使用されたキーとプロセスに関する情報が含まれているサブ要素を含めることができます。  XML の暗号化を使用すると、ドキュメントに複数の暗号化された要素を含められるだけでなく、要素を複数回暗号化することができます。  この手順のコード例は、\<`EncryptedData`\> 要素の作成方法と共に、後の復号化時に使用するいくつかのその他のサブ要素の作成方法を示しています。  
  
 この例では、2 つのキーを使用して XML 要素を復号化します。  [Makecert.exe \(証明書作成ツール\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md) を使用してテストの X.509 証明書を生成し、この証明書を証明書ストアに保存します。  この例では、プログラムを使用して証明書を取得し、これを使用して <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> メソッドで XML 要素を暗号化します。  内部的には、<xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> メソッドは別のセッション キーを作成し、これを使用して XML ドキュメントを暗号化します。  このメソッドでは、セッション キーを暗号化し、新しい \<`EncryptedData`\> 要素内に暗号化された XML と共に保存します。  
  
 XML 要素を復号化するには、<xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> メソッドを呼び出します。これにより、ストアから X.509 証明書が自動的に取得され、必要な復号化が実行されます。  この手順を使用して暗号化された XML 要素を復号化する方法の詳細については、「[方法 : X.509 証明書で XML 要素を復号化する](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)」を参照してください。  
  
 この例は、複数のアプリケーションが暗号化されたデータを共有する必要がある状況や、1 つのアプリケーションが、実行する時間の間に暗号化されたデータを保存する必要がある状況に適しています。  
  
### X.509 証明書で XML 要素を暗号化するには  
  
1.  [Makecert.exe \(証明書作成ツール\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md) を使用してテストの X.509 証明書を生成し、ローカル ユーザーのストアに配置します。  交換キーを生成する必要があり、このキーをエクスポート可能にする必要があります。  次のコマンドを実行します。  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  <xref:System.Security.Cryptography.X509Certificates.X509Store> オブジェクトを作成し、このオブジェクトを現在のユーザー ストアを開くように初期化します。  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  ストアを読み取り専用モードで開きます。  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> を、ストア内のすべての証明書で初期化します。  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  ストア内の証明書を列挙し、適切な名前を持つ証明書を検索します。  この例では、証明書の名前は `"CN=XML_ENC_TEST_CERT"` です。  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  証明書が見つかったら、ストアを閉じます。  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。  <xref:System.Xml.XmlDocument> オブジェクトには、暗号化する XML 要素が含まれています。  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  <xref:System.Xml.XmlDocument> オブジェクトで指定された要素を検索し、暗号化する要素を表す新しい <xref:System.Xml.XmlElement> オブジェクトを作成します。  この例では、`"creditcard"` 要素が暗号化されます。  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <xref:System.Security.Cryptography.Xml.EncryptedXml> クラスのインスタンスを新規作成し、これを使用して、X.509 証明書によって指定された要素を暗号化します。  <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> メソッドは、暗号化された要素を、<xref:System.Security.Cryptography.Xml.EncryptedData> オブジェクトとして返します。  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. 元の <xref:System.Xml.XmlDocument> オブジェクトの要素を <xref:System.Security.Cryptography.Xml.EncryptedData> 要素に置き換えます。  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <xref:System.Xml.XmlDocument> オブジェクトを保存します。  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## コードのコンパイル  
  
-   この例をコンパイルするには、`System.Security.dll` への参照を含める必要があります。  
  
-   名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。  
  
## .NET Framework セキュリティ  
 この例で使用される X.509 証明書は、テスト専用です。  アプリケーションは、信頼された証明機関が生成する X.509 証明書、または Microsoft Windows 証明書サーバーによって生成された証明書を使用する必要があります。  
  
## 参照  
 <xref:System.Security.Cryptography.Xml>   
 [方法 : X.509 証明書で XML 要素を復号化する](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)