---
title: "アプリケーションの構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# アプリケーションの構成
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、.NET 構成システムを使用して、コンピューターとアプリケーションのスコープでサービスを構成できるようにします。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって定義された構成設定は、`<system.serviceModel>` セクション グループにあります。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの構成方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、次のトピックを参照してください。  
  
-   [サービスの構成](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 アプリケーション定義の構成設定は、`<appSettings>` セクション グループで定義されます。.NET 構成ファイルのアプリケーション設定[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[\<appSettings\>](http://go.microsoft.com/fwlink/?LinkId=95159)」を参照してください。  
  
## 構成エディターの使用  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [構成エディター ツール \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) のグラフィカル ユーザー インターフェイスを使用して、管理者と開発者は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの構成設定を作成および変更できます。このツールを使用すると、XML 構成ファイルを直接編集せずに、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のバインディング、動作、サービス、および診断の設定を管理できます。  
  
## Visual Studio の構成ファイルの編集  
 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス プロジェクトの構成ファイルを編集するには、**ソリューション エクスプローラー**で構成ファイルを右クリックし、**\[WCF 構成の編集\]** コンテキスト メニュー項目を選択します。これにより[構成エディター ツール \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) が起動されます。  
  
> [!NOTE]
>  [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web サービス プロジェクトの構成ファイルを**ソリューション エクスプローラー**で右クリックして編集する場合は、**\[Edit WCF Config\]** コンテキスト メニュー項目が表示されません。この問題を回避するには、**\[ツール\]** メニューをクリックし、**\[WCF Service Config Editor\]** を選択します。この操作を行った後は、構成ファイルを右クリックして **\[Edit WCF Config\]** コンテキスト メニュー項目を表示できます。  
  
## 参照  
 [構成エディター ツール \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)   
 [サービスの構成](../../../../docs/framework/wcf/configuring-services.md)   
 [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)