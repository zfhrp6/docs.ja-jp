---
title: "LINQ to XML のセキュリティ (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: d99b4af2-d447-4a3b-991b-6da0231a8637
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 559bf330640840a310ff947cac118953d1df1a13
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-security-visual-basic"></a>LINQ to XML のセキュリティ (Visual Basic)
ここでは、LINQ to XML に関連するセキュリティの問題について説明し、 セキュリティ上の脆弱性を緩和するためのガイドラインを紹介します。  
  
## <a name="linq-to-xml-security-overview"></a>LINQ to XML のセキュリティの概要  
 LINQ to XML は、厳密なセキュリティ要件が必要なサーバー側アプリケーション向けというよりも、プログラミングの利便性に重点を置いて設計されています。 ほとんどの XML のシナリオでは、サーバーにアップロードされる信頼できない XML ドキュメントではなく、信頼できる XML ドキュメントが処理されます。 LINQ to XML は、こうした一般的なシナリオに最適化されています。  
  
 マイクロソフトは、のインスタンスを使用することをお勧め場合は、不明なソースから信頼されていないデータを処理する必要があります、<xref:System.Xml.XmlReader>既知 XML サービス拒否 (DoS) 攻撃を除外するように構成されたクラスです</xref:System.Xml.XmlReader>。  
  
 構成した場合、<xref:System.Xml.XmlReader>サービス拒否攻撃を軽減するために、LINQ to XML ツリーを設定し、XML への LINQ のプログラマの生産性向上のメリットもそのリーダーを使用することができます</xref:System.Xml.XmlReader>。 このように、セキュリティの問題を緩和するように構成されたリーダーを作成し、その構成済みのリーダーを使用して XML ツリーをインスタンス化する方法は、多くの軽減技法で利用されています。  
  
 XML は、ドキュメントのサイズ、深さ、要素名のサイズなどの制限がないため、サービス拒否攻撃に対して本質的に脆弱です。 XML の処理に使用するコンポーネントに関係なく、リソースが過剰に使用されている場合は、常にアプリケーション ドメインを再利用できるようにしておく必要があります。  
  
## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>XML、XSD、XPath、および XSLT の攻撃の緩和  
 LINQ to XML の作成<xref:System.Xml.XmlReader>と<xref:System.Xml.XmlWriter></xref:System.Xml.XmlWriter></xref:System.Xml.XmlReader>対象 LINQ to XML が拡張メソッドによって XSD と XPath をサポートしている、<xref:System.Xml.Schema?displayProperty=fullName>と<xref:System.Xml.XPath?displayProperty=fullName>名前空間</xref:System.Xml.XPath?displayProperty=fullName></xref:System.Xml.Schema?displayProperty=fullName>。 使用して、 <xref:System.Xml.XmlReader>、 <xref:System.Xml.XPath.XPathNavigator>、および<xref:System.Xml.XmlWriter>クラスは LINQ to XML と組み合わせて、XML ツリーを変換する XSLT を呼び出すことができます</xref:System.Xml.XmlWriter></xref:System.Xml.XPath.XPathNavigator></xref:System.Xml.XmlReader>。  
  
 安全性の低い環境で運用している場合があるさまざまな XML に関連付けられているセキュリティの問題とのクラスを使用して<xref:System.Xml?displayProperty=fullName>、 <xref:System.Xml.Schema?displayProperty=fullName>、 <xref:System.Xml.XPath?displayProperty=fullName>、 <xref:System.Xml.Xsl?displayProperty=fullName>.</xref:System.Xml.Xsl?displayProperty=fullName> </xref:System.Xml.XPath?displayProperty=fullName> </xref:System.Xml.Schema?displayProperty=fullName> </xref:System.Xml?displayProperty=fullName> そのような問題の一部を次に示します。  
  
-   XSD、XPath、および XSLT は文字列に基づく言語であり、時間やメモリを大量に消費する操作を指定することができます。 信頼されていないソースの XSD、XPath、または XSLT の文字列を受け取る場合、アプリケーション プログラマは、その文字列が悪意のあるものでないかどうかを検証する必要があります。また、その文字列の評価によってシステム リソースが過剰に消費されないように監視し、過剰に消費された場合はその状況を緩和する必要があります。  
  
-   XSD スキーマ (インライン スキーマを含む) は、サービス拒否攻撃に対して本質的に脆弱です。信頼できないソースのスキーマは受け入れないようにしてください。  
  
-   XSD や XSLT には他のファイルへの参照が含まれている場合があり、それらの参照が原因で、ゾーンやドメインを越えた攻撃を受ける可能性があります。  
  
-   DTD 内の外部エンティティが原因で、ゾーンやドメインを越えた攻撃を受ける可能性があります。  
  
-   DTD はサービス拒否攻撃に対して脆弱です。  
  
-   極端に階層の深い XML ドキュメントが原因で、サービス拒否攻撃を受ける可能性があります。XML ドキュメントの階層を制限することをお勧めします。  
  
-   など、サポート コンポーネントは受け入れない<xref:System.Xml.NameTable>、 <xref:System.Xml.XmlNamespaceManager>、および<xref:System.Xml.XmlResolver>信頼できないアセンブリからのオブジェクト</xref:System.Xml.XmlResolver></xref:System.Xml.XmlNamespaceManager></xref:System.Xml.NameTable>。  
  
-   サイズの大きなドキュメントによる攻撃を緩和するためにデータをチャンク単位で読み取ります。  
  
-   XSLT スタイル シート内のスクリプト ブロックが原因で、多くの攻撃を受ける場合があります。  
  
-   動的な XPath 式を作成する場合は事前に慎重に検証します。  
  
## <a name="linq-to-xml-security-issues"></a>LINQ to XML のセキュリティの問題  
 ここに示されているセキュリティの問題には、特に優先順位はありません。 すべての問題が重要であり、それぞれに適切に対処する必要があります。  
  
 権限の昇格攻撃が成功すると、悪意のあるアセンブリがその環境をより自由に制御できるようになります。 その結果、データの公開攻撃やサービス拒否攻撃などを受ける可能性があります。  
  
 アプリケーションでは、権限のないユーザーにデータを公開しないようにする必要があります。  
  
 サービス拒否攻撃を受けると、XML パーサーや LINQ to XML がメモリや CPU 時間を大量に消費するようになります。 サービス拒否攻撃は、権限の昇格攻撃やデータの公開攻撃ほど重大に捉えられていませんが、 信頼できないソースからの XML ドキュメントをサーバーで処理する必要があるシナリオでは重大な問題です。  
  
### <a name="exceptions-and-error-messages-might-reveal-data"></a>例外やエラー メッセージによってデータが漏洩する可能性がある  
 変換されるデータ、ファイル名、実装の詳細などのデータが、エラーの説明から漏洩する可能性があります。 信頼されていない呼び出し元に対してはエラー メッセージが表示されないようにする必要があります。 すべてのエラーをキャッチして、カスタム エラー メッセージでエラーを報告するようにしてください。  
  
### <a name="do-not-call-codeaccesspermissionsassert-in-an-event-handler"></a>イベント ハンドラーで CodeAccessPermissions.Assert を呼び出さない  
 アセンブリの権限は、低い場合もあれば高い場合もあります。 高い権限を持つアセンブリは、コンピューターやその環境をより自由に制御できます。  
  
 高い権限を持つアセンブリのコードを呼び出す場合<xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>のイベント ハンドラーをし、XML ツリーが渡される悪意のあるアセンブリにことが制限されたアクセス許可、悪意のあるアセンブリが発生するイベントが発生する</xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>。 このイベントは、高い権限を持つアセンブリ内のコードを実行するため、悪意のあるアセンブリが高度な特権で動作するようになります。  
  
 マイクロソフトは呼び出さないようにすることをお勧め<xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>イベント ハンドラーで</xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>。  
  
### <a name="dtds-are-not-secure"></a>DTD は安全ではない  
 DTD 内のエンティティは、本質的に安全ではありません。 DTD を含む悪意のある XML ドキュメントが原因で、サービス拒否攻撃を受け、メモリと CPU 時間のすべてがパーサーによって使用されるといった状況が発生する可能性があります。 このため、LINQ to XML では DTD の処理が既定で無効になっています。 信頼されていないソースの DTD は受け入れないようにしてください。  
  
 たとえば、DTD を参照する XML ファイルと DTD ファイルをアップロードすることを Web ユーザーに対して許可する Web アプリケーションは、信頼されていないソースの DTD を受け入れる例の&1; つです。 この場合は、ファイルの検証の際に、悪意のある DTD によってサーバーに対するサービス拒否攻撃が行われる可能性があります。 そのほか、匿名 FTP アクセスが許可されているネットワーク共有の DTD を参照する場合も、信頼されていないソースの DTD を受け入れる例になります。  
  
### <a name="avoid-excessive-buffer-allocation"></a>過剰なバッファーの割り当てを回避する  
 アプリケーション開発者は、極端に大きなデータ ソースが原因でリソース消費攻撃やサービス拒否攻撃を受ける可能性があることを認識しておく必要があります。  
  
 悪意のあるユーザーによって非常に大きな XML ドキュメントが送信されたり、アップロードされたりすると、LINQ to XML がシステム リソースを過剰に消費するようになります。 このような状況が、サービス拒否攻撃の原因となる場合があります。 これを防ぐためには、設定することができます、<xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=fullName>プロパティには、読み込むことのできるドキュメントのサイズが制限されたリーダーを作成します</xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=fullName>。 その後、そのリーダーを使用して XML ツリーを作成します。  
  
 たとえば、最大値が信頼できないソースからの XML ドキュメントのサイズを想定していることがわかっている場合は 50 K バイト未満、設定<xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=fullName>100,000</xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=fullName> 。 これにより、XML ドキュメントの処理を妨げずに、大量のメモリを消費するドキュメントがアップロードされるサービス拒否攻撃の脅威を緩和できます。  
  
### <a name="avoid-excess-entity-expansion"></a>過剰なエンティティの展開を回避する  
 DTD の使用時に発生するサービス拒否攻撃の&1; つに、エンティティを過剰に展開するドキュメントによる攻撃があります。 これを防ぐためには、設定することができます、<xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=fullName>プロパティには、エンティティの展開により生成される文字の数が制限されたリーダーを作成します</xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=fullName>。 その後、そのリーダーを使用して XML ツリーを作成します。  
  
### <a name="limit-the-depth-of-the-xml-hierarchy"></a>XML 階層の深さを制限する  
 サービス拒否攻撃は、極端に深い階層を持つドキュメントが送信された場合にも発生します。 これを防ぐためには、ラップすることができます、<xref:System.Xml.XmlReader>要素の深さをカウントする独自のクラスにします</xref:System.Xml.XmlReader>。 これにより、要素の深さが事前に設定したレベルを超えている場合に、その悪意のあるドキュメントの処理を終了できます。  
  
### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>信頼されていない XmlReader や XmlWriter の実装から保護する  
 管理者が、外部から指定されたいずれかを確認する必要があります<xref:System.Xml.XmlReader>または<xref:System.Xml.XmlWriter>の実装は、厳密な名前があるし、マシンの構成に登録されている</xref:System.Xml.XmlWriter></xref:System.Xml.XmlReader>。 これにより、リーダーやライターを装った悪意のあるコードが読み込まれるのを防ぐことができます。  
  
### <a name="periodically-free-objects-that-reference-xname"></a>XName を参照するオブジェクトを定期的に解放する  
 ある種の攻撃を防ぐために、アプリケーション プログラマを参照するすべてのオブジェクトを解放する必要があります、<xref:System.Xml.Linq.XName>を定期的にアプリケーション ドメイン内のオブジェクト</xref:System.Xml.Linq.XName>。  
  
### <a name="protect-against-random-xml-names"></a>ランダムな XML 名から保護する  
 信頼されていないソースからデータを取得するアプリケーションを使用して、<xref:System.Xml.XmlReader>はカスタム コードでラップするランダムな XML 名と名前空間の検査します</xref:System.Xml.XmlReader>。 これにより、ランダムな XML 名や XML 名前空間が検出された場合に、アプリケーションでその悪意のあるドキュメントの処理を終了できます。  
  
 特定の名前空間の名前の数 (および名前空間に含まれない名前の数) を制限することをお勧めします。  
  
### <a name="annotations-are-accessible-by-software-components-that-share-a-linq-to-xml-tree"></a>LINQ to XML ツリーを共有するソフトウェア コンポーネントは注釈にアクセスできる  
 LINQ to XML を使用すると、さまざまなアプリケーション コンポーネントによって XML データの読み込み、検証、クエリ、変換、更新、および保存が行われる処理パイプラインを構築できます。XML データは、XML ツリーとしてコンポーネント間で受け渡されます。 この場合、オブジェクトを読み込んで XML テキストにシリアル化する際のオーバーヘッドがパイプラインの最後にしか発生しないため、パフォーマンスを最適化することができます。 ただし、開発者は、あるコンポーネントによって作成される注釈やイベント ハンドラーはすべて、他のコンポーネントからもアクセスできることを認識しておく必要があります。 このことは、異なる信頼レベルのコンポーネントが混在している場合に数々の脆弱性の原因になります。 信頼レベルの低いコンポーネントが含まれる場合に安全なパイプラインを構築するには、信頼されていないコンポーネントにデータを渡す前に LINQ to XML オブジェクトを XML テキストにシリアル化する必要があります。  
  
 ある程度のセキュリティが共通言語ランタイム (CLR) によって提供されます。 たとえば、プライベート クラスを含まないコンポーネントは、そのクラスによってキー指定された注釈にはアクセスできません。 ただし、注釈を読み取れないコンポーネントでも、注釈を削除することはできます。 このことが、改ざん攻撃に利用される可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [プログラミング ガイド (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
