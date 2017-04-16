---
title: "方法: データ サービス参照を追加する (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, 構成"
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 方法: データ サービス参照を追加する (WCF Data Services)
Visual Studio の **\[サービス参照の追加\]** ダイアログを使用して、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] に参照を追加できます。  参照をデータ サービスに追加すると、Visual Studio で開発したクライアント アプリケーションのデータ サービスに容易にアクセスできます。  この手順を完了すると、データ サービスから取得されたメタデータに基づいてデータ クラスが生成されます。  詳細については、「[データ サービス クライアント ライブラリの生成](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)」を参照してください。  
  
### データ サービス参照を追加するには  
  
1.  \(オプション\) データ サービスがソリューションの一部ではなく、実行していない場合は、データ サービスを開始して、データ サービスの URI を記録します。  
  
2.  クライアント プロジェクトを右クリックして、**\[サービス参照の追加\]** をクリックします。  
  
3.  データ サービスが現在のソリューションの一部である場合は、**\[探索\]** をクリックします。  
  
     または  
  
     **\[アドレス\]** ボックスにデータ サービスのベース URL \(`http://localhost:1234/Northwind.svc` など\) を入力して **\[移動\]** をクリックします。  
  
4.  **\[OK\]** をクリックします。  
  
     新しいコード ファイルが追加されます。このコード ファイルには、データ サービス リソースにアクセスし、オブジェクトとしてデータ サービス リソースと対話するデータ クラスが含まれています。  
  
## 参照  
 [クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)