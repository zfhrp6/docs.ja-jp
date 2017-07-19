---
title: "方法: Entity Framework プロバイダーでフィードをカスタマイズする (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, カスタマイズ"
  - "WCF Data Services, フィードのカスタマイズ"
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 方法: Entity Framework プロバイダーでフィードをカスタマイズする (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、データ サービス応答の Atom シリアル化をカスタマイズして、AtomPub プロトコルで定義されている未使用の要素にエンティティのプロパティをマップできます。  このトピックでは、Entity Framework を使用して、.edmx ファイルで定義されているデータ モデルのエンティティ型のマッピング属性を定義する方法について説明します。  詳細については、「[フィードのカスタマイズ](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)」を参照してください。  
  
 このトピックでは、ツールによって生成された .edmx file ファイルを手動で変更します \(このファイルには、データ モデルが含まれます\)。  エンティティ デザイナーではデータ モデルへの拡張がサポートされていないので、このファイルは手動で変更する必要があります。  Entity Data Model ツールによって生成される .edmx ファイルの詳細については、「[.edmx File Overview](http://msdn.microsoft.com/ja-jp/f4c8e7ce-1db6-417e-9759-15f8b55155d4)」を参照してください。  このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。  このサービスおよびクライアント データ クラスは、[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
### Northwind.edmx ファイルを手動で変更してフィードのカスタマイズ属性を追加するには  
  
1.  **ソリューション エクスプローラー**で `Northwind.edmx` ファイルを右クリックして、**\[プログラムから開く\]** をクリックします。  
  
2.  **\[Northwind.edmx を開くアプリケーションの選択\]** ダイアログ ボックスで、**\[XML エディター\]** をクリックし、**\[OK\]** をクリックします。  
  
3.  `ConceptualModels` 要素を見つけて、フィードのカスタマイズ マッピング属性を含む次の要素で既存の `Customers` エンティティ型を置き換えます。  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4.  変更を保存して Northwind.edmx ファイルを閉じます。  
  
5.  \(オプション\) Northwind.edmx ファイルを右クリックして、**\[カスタム ツールの実行\]** をクリックします。  
  
     オブジェクト レイヤー ファイルが再生成されます。このファイルが必要になる場合があります。  
  
6.  プロジェクトを再コンパイルします。  
  
## 使用例  
 前の例では、`http://myservice/` `Northwind.svc/Customers('ALFKI')` という URI に対して次の結果が返されます。  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## 参照  
 [Entity Framework プロバイダー](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)