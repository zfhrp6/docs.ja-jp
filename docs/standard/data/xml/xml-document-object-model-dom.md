---
title: "XML ドキュメント オブジェクト モデル (DOM)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ff91e929876ceec8512e962b88795b6a8a29f3d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xml-document-object-model-dom"></a>XML ドキュメント オブジェクト モデル (DOM)
XML ドキュメント オブジェクト モデル (DOM) クラスは、XML ドキュメントのメモリ内表現です。 DOM を使用すると、XML ドキュメントの読み込み、操作、および変更をプログラムから実行できます。 **XmlReader**クラスも XML を読み取ります。 ただし、非キャッシュ、順方向専用、読み取り専用アクセスを提供します。 つまり、属性の値または要素、または挿入し、使用してノードを削除する機能の内容を編集する機能がないこと、 **XmlReader**です。 DOM の主な機能は編集です。 XML データは、通常、メモリ上では構造的に表現されますが、実際の XML データをファイルに保存したり、別のオブジェクトから取り込む場合は、直線的な形式で格納されます。 XML データの例を次に示します。  
  
## <a name="input"></a>入力  
  
```xml  
<?xml version="1.0"?>  
  <books>  
    <book>  
        <author>Carson</author>  
        <price format="dollar">31.95</price>  
        <pubdate>05/01/2001</pubdate>  
    </book>  
    <pubinfo>  
        <publisher>MSPress</publisher>  
        <state>WA</state>  
    </pubinfo>  
  </books>   
```  
  
 この XML データが DOM 構造に読み込まれるとき、メモリがどのように構造化されるかを次の図に示します。  
  
 ![XML ドキュメントの構造](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")  
XML ドキュメントの構造  
  
 この図では、各円と呼ばれるノードを表す XML ドキュメントの構造内で、 **XmlNode**オブジェクト。 **XmlNode**オブジェクトが、DOM ツリーの基本オブジェクト。 **XmlDocument**を拡張するクラス**XmlNode**が全体として (たとえばをメモリに読み込むか、XML をファイルに保存ドキュメントに対する操作を実行するためのメソッドをサポートしています。 さらに、 **XmlDocument**を表示して、XML ドキュメント全体のノードを操作する手段を提供します。 両方**XmlNode**と**XmlDocument**パフォーマンスと使いやすさの拡張機能がありするメソッドとプロパティ。  
  
-   要素ノード、エンティティ参照ノードなど、DOM に固有のノードへのアクセスと変更。  
  
-   要素ノードのテキストなど、ノードに格納されている情報およびノード全体の取得。  
  
    > [!NOTE]
    >  構造体、または編集、DOM によって提供される機能がアプリケーションに必要としない場合、 **XmlReader**と**XmlWriter**クラスは、XML を非キャッシュ、前方参照専用のストリーム アクセスを提供します。 詳細については、<xref:System.Xml.XmlReader> および <xref:System.Xml.XmlWriter> を参照してください。  
  
 **ノード**オブジェクト メソッドとプロパティと同様の基本的なと適切に定義された特徴セットがあります。 オブジェクトが持つ特性のいくつかを次に示します。  
  
-   ノードは 1 つの親ノードを持っています。親ノードはノードの 1 つ上のノードです。 ドキュメント ルートは最上位のノードであり、ドキュメント自身とドキュメント フラグメントしか格納されていないため、親ノードを持っていないノードはドキュメント ルートだけです。  
  
-   ほとんどのノードは、複数の子ノードを持つことができます。子ノードは、ノードの 1 つ下のノードです。 子ノードを持つことができるノード型の一覧を次に示します。  
  
    -   **ドキュメント**  
  
    -   **Documentfragment**  
  
    -   **EntityReference**  
  
    -   **要素**  
  
    -   **属性**  
  
     **XmlDeclaration**、**表記**、**エンティティ**、 **CDATASection**、**テキスト**、 **コメント**、 **ProcessingInstruction**、および**DocumentType**ノードに子ノードがありません。  
  
-   ダイアグラム ビューで表される、同じレベルにあるノード、 **book**と**pubinfo**は兄弟です。  
  
 DOM の特性の 1 つは、属性の取り扱い方法にあります。 属性は、互いに親子関係や兄弟関係を持つノードではありません。 属性は要素ノードのプロパティと見なされ、名前と値ペアから構成されます。 たとえば、要素 `format="dollar` に関連付けられている `price`" という形式の XML データがある場合は、単語 `format` が名前になり、`format` 属性の値は `dollar` になります。 取得する、`format="dollar"`の属性、**価格** ノードを呼び出す、 **GetAttribute**メソッドにカーソルがあるときに、`price`要素ノードです。 詳細については、次を参照してください。 [、DOM 内の属性へのアクセス](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md)です。  
  
 XML をメモリに読み込むと、ノードが作成されます。 ただし、すべてのノードが同じタイプというわけではありません。 XML の要素の規則と構文は、処理命令の規則と構文とは異なります。 したがって、さまざまなデータが読み込まれるときに、個々のノードにノード型が割り当てられます。 このノード型によって、ノードの特性と機能が決定されます。  
  
 メモリ内で生成されるノードの種類の詳細については、次を参照してください。 [XML ノードの種類](../../../../docs/standard/data/xml/types-of-xml-nodes.md)です。 ノード ツリーに作成されたオブジェクトの詳細については、次を参照してください。[オブジェクト階層の XML データへのマップ](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)です。  
  
 Microsoft では、XML ドキュメントの操作を容易にするために、W3C (World Wide Web Consortium) DOM Level 1 および Level 2 で規定されている API を拡張しています。 W3C の標準を完全にサポートする一方で、追加のクラス、メソッド、プロパティにより、W3C の XML DOM で実現できる以上の機能が付加されています。 新しいクラスを使用すると、リレーショナル データにアクセスし、ADO.NET との同期をとりながら、データを XML として公開できます。 詳細については、次を参照してください。 [DataSet と XmlDataDocument の同期](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)です。  
  
 DOM が最も役に立つのは、XML データをメモリに読み込み、その構造を変更したり、ノードを追加または削除したり、要素内のテキストとしてノードが保持しているデータを変更したりする場合です。 ただし、他のクラスも用意されており、シナリオによっては DOM より高速になる場合もあります。 XML へのアクセスを高速かつ非キャッシュで順方向専用ストリームを使用して、 **XmlReader**と**XmlWriter**です。 カーソル モデルとランダム アクセスを必要がある場合と**XPath**を使用して、 **XPathNavigator**クラスです。  
  
## <a name="see-also"></a>関連項目  
 [XML ノードの種類](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
 [オブジェクト階層の XML データへのマップ](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)
