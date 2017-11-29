---
title: "アプリケーションの構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f22fac02616070ecd6498ad0e158782001681ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-your-application"></a>アプリケーションの構成
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、.NET 構成システムを使用して、コンピューターとアプリケーションのスコープでサービスを構成できるようにします。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって定義された構成設定は、`<system.serviceModel>` セクション グループにあります。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] サービスの構成方法[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]、次のトピックを参照してください。  
  
-   [サービスの構成](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 アプリケーション定義の構成設定は、`<appSettings>` セクション グループで定義されています。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)].NET 構成ファイル内のアプリケーション設定を参照してください[ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159)です。  
  
## <a name="using-the-configuration-editor"></a>構成エディターの使用  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)][構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)作成および構成設定を変更するには、管理者および開発者[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]services のグラフィカル ユーザー インターフェイスを使用します。 このツールを使用すると、XML 構成ファイルを直接編集せずに、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のバインディング、動作、サービス、および診断の設定を管理できます。  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Visual Studio の構成ファイルの編集  
 構成ファイルを編集する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]でサービス プロジェクト[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]で右クリック**ソリューション エクスプ ローラー**を選択し、 **Edit WCF Config**コンテキスト メニュー項目。 これにより、起動、[構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)です。  
  
> [!NOTE]
>  構成ファイルを編集する場合、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web サービス プロジェクトの[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]で右クリックして**ソリューション エクスプ ローラー**、ことに注意して、 **Edit WCF Config**コンテキスト メニュー項目がありません. この問題を回避するには、をクリックして、**ツール**] メニューの [選択**WCF Service Config Editor**です。 その後、構成ファイルを右クリックして使用することができます、 **Edit WCF Config**コンテキスト メニュー項目。  
  
## <a name="see-also"></a>関連項目  
 [構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [サービスの構成](../../../../docs/framework/wcf/configuring-services.md)  
 [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
