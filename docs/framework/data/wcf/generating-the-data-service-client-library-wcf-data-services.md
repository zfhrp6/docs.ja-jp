---
title: "データ サービス クライアント ライブラリの生成 (WCF Data Services) | Microsoft Docs"
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
  - "[サービス参照の追加] ダイアログ ボックス"
  - "クライアント アプリケーション, WCF Data Services"
  - "WCF Data Services, クライアント ライブラリ"
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# データ サービス クライアント ライブラリの生成 (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] を実装しているデータ サービスは、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードによって公開されているデータ モデルが記述されたサービス メタデータ ドキュメントを返すことがあります。  詳細については、「[OData: サービス メタデータ ドキュメント](http://go.microsoft.com/fwlink/?LinkId=186070)」を参照してください。Visual Studio の **\[サービス参照の追加\]** ダイアログを使用すると、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ベースのサービスに参照を追加できます。  このツールを使用してクライアント プロジェクト内の [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] によって返されるメタデータに参照を追加すると、次のアクションが実行されます。  
  
-   データ サービスからのサービス メタデータ ドキュメントが要求され、返されたメタデータが解釈されます。  
  
    > [!NOTE]
    >  返されたメタデータは、クライアント プロジェクトに .edmx ファイルとして保存されます。  .edmx ファイルは、Entity Framework で使用される .edmx ファイルと形式が異なるので、Entity Data Model デザイナーを使用して開くことができません。  このメタデータ ファイルは、XML エディターまたは任意のテキスト エディターを使用して表示できます。  詳細については、「[\[MC\-EDMX\]: データ サービスのパッケージ形式のエンティティ データ モデル](http://go.microsoft.com/fwlink/?LinkID=178833)」仕様を参照してください。  
  
-   <xref:System.Data.Services.Client.DataServiceContext> から継承するエンティティ コンテナー クラスとしてサービスの表現が生成されます。  この生成されたエンティティ コンテナー クラスは、Entity Data Model ツールが生成するエンティティ コンテナーに似ています。  詳細については、「[Object Services Overview \(Entity Framework\)](http://msdn.microsoft.com/ja-jp/43014cf9-c9cb-4538-bfbb-197820b60038)」を参照してください。  
  
-   サービス メタデータ内で見つかったデータ モデル型のデータ クラスが生成されます。  
  
-   `System.Data.Services.Client` アセンブリへの参照がプロジェクトに追加されます。  
  
 詳細については、「[方法: データ サービス参照を追加する](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)」を参照してください。  
  
 クライアント データ サービス クラスは、コマンド プロンプトで [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) ツールを使用して生成することもできます。  詳細については、「[方法: クライアント データ サービス クラスを手動で生成する](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)」を参照してください。  
  
## クライアント データ型のマッピング  
 Visual Studio の **\[サービス参照の追加\]** ダイアログまたは `DataSvcUtil.exe` ツールを使用して、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードに基づいてクライアント データ クラスを生成する場合、次のように .NET Framework データ型がデータ モデルのプリミティブ型にマップされます。  
  
|データ モデル型|.NET Framework データ型|  
|--------------|-------------------------|  
|`Edm.Binary`|<xref:System.Byte> `[]`|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 詳細については、「[OData: プリミティブ データ型](http://go.microsoft.com/fwlink/?LinkId=186072)」を参照してください。  
  
## 参照  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)   
 [クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)