---
title: "XML とリレーショナル データおよび ADO.NET との統合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6ebb1a1-f2ca-49b9-92c9-0150940cf6e6
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5d03a0ca7518b06c08d98967d7c5ae864f1c04ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="xml-integration-with-relational-data-and-adonet"></a>XML とリレーショナル データおよび ADO.NET との統合
**XmlDataDocument**クラスは、派生クラスの**XmlDocument**、XML データが含まれています。 利点、 **XmlDataDocument**リレーショナル データと階層データ間のブリッジを提供できることです。 **XmlDocument**に連結できる、**データセット**2 つのクラスに含まれるデータに加えられた変更を同期できるは、両方のクラスとします。 **XmlDocument**にバインドされている、**データセット**XML とリレーショナル データを統合することができ、データ、XML、またはリレーショナル形式で表現する必要はありません。 両方の処理ができ、一方のデータ表現だけに制限されることもありません。  
  
 2 つの形式でデータが使用できる利点は次のとおりです。  
  
-   XML ドキュメントの構造部分はデータセットに対応付けることができ、効率的な格納、インデックス付け、および検索ができる。  
  
-   リレーション形式で格納された XML データに対して、カーソル モデルを使用して、効率的な変換、検証、および移動ができる。 ときに、実行できますより効率的によりに、XML が格納されている場合は、リレーショナル構造、 **XmlDocument**モデル。  
  
-   **データセット**XML の一部を格納することができます。 つまり、使用することができます**XPath**または**XslTransform**に保存する、**データセット**要素や関心のある属性だけです。 そこから、変更できるよう、データのより小さく、フィルター選択されたサブセットにでより大きなデータを反映する変更内容を**XmlDataDocument**です。  
  
 読み込まれたデータの変換を実行することも、**データセット**SQL Server からです。 別のオプションは、.NET Framework クラスからスタイル マネージ WinForm をバインドして、WebForm のコントロールを**データセット**ですが、XML 入力ストリームから設定します。  
  
 サポートするだけでなく**XslTransform**、 **XmlDataDocument**リレーショナル データを公開**XPath**クエリおよび検証します。  基本的には、すべての XML サービスをリレーショナル データで利用でき、コントロールの連結やコード生成などのすべてのリレーショナル機能を XML に基づく構造化データで、XML の厳密性を損なうことなく利用できます。  
  
 **XmlDataDocument**から継承されますが、 **XmlDocument**、W3C DOM の実装を提供 ファクトを**XmlDataDocument**が関連付けられ、そのデータのサブセットを格納、**データセット**制限またはとしての使用を変更していない、 **XmlDocument**任意の方法でします。 使用する記述されたコード、 **XmlDocument**に対して動作が変更されない、 **XmlDataDocument**です。 **データセット**テーブル、列、リレーション、および制約を定義することで、同じデータのリレーショナル ビューを提供し、スタンドアロンのメモリ内のユーザーのデータ ストアです。  
  
 次の図は、XML データを持つことを別の関連付けには、**データセット**と**XmlDataDocument**です。  
  
 ![XML データセット](../../../../docs/standard/data/xml/media/xmlintegrationwithrelationaldataandadodotnet.gif "xmlIntegrationWithRelationalDataAndADOdotNet")  
  
 図に示す XML データを直接に読み込めること、**データセット**、リレーショナルな方法で XML を直接操作できます。 または、これは、DOM の派生クラスに、XML を読み込むことができます、 **XmlDataDocument**、およびその後読み込みと同期されている、**データセット**です。 **データセット**と**XmlDataDocument** 1 つのセット上で同期が、データの 1 つのストア内のデータに加えられた変更は他方のストアに反映されます。  
  
 **XmlDataDocument**からすべての編集と移動機能を継承、 **XmlDocument**です。 ありますを使用する場合、 **XmlDataDocument**と同期されているその継承された機能と、**データセット**に直接 XML を読み込むよりも適切なオプションは、**データセット**. 次の表に、読み込みに使用する方法を選択する際に考慮すべき項目、**データセット**です。  
  
|XML を DataSet に直接読み込む方がよい場合|XmlDataDocument と DataSet の同期をとる方がよい場合|  
|----------------------------------------------|-----------------------------------------------------------|  
|内のデータのクエリ、**データセット**は XPath よりも SQL を使用して容易に行えます。|内のデータに対して XPath クエリが必要、**データセット**です。|  
|ソース XML 内での要素の順序を保つ必要がない。|ソース XML 内での要素の順序を保つ必要がある。|  
|要素間の空白や形式をソース XML で保持する必要がない。|空白や形式をソース XML で保持する必要がある。|  
  
 読み込みと XML の記述に直接および out の場合、**データセット**、ニーズに対応するを参照してください[XML からの DataSet の読み込み](../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)と[XML データとしての DataSet の書き込み](../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)です。  
  
 読み込んでいる場合、**データセット**から、 **XmlDataDocument** 、ニーズに対応するを参照してください[Datasetwith XML ドキュメントを同期する](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)です。  
  
## <a name="see-also"></a>関連項目  
 [DataSet での XML の使用](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
