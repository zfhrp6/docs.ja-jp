---
title: "JSON Web トークン ハンドラー パッケージのダウンロード | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
caps.latest.revision: 3
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 3
---
# JSON Web トークン ハンドラー パッケージのダウンロード
このトピックでは、JSON Web トークン ハンドラーをダウンロードしてプロジェクトで使用する方法について説明します。  
  
## JSON Web トークン ハンドラーのダウンロード  
 JSON Web トークン ハンドラー拡張機能は、プロジェクトに必要なアセンブリと参照を追加する NuGet パッケージとして入手できます。  まだ NuGet がインストールされていない場合は、[nuget.org](http://nuget.org) にアクセスしてインストールしてください。  NuGet の「[JSON Web Token Handler \(JSON Web トークン ハンドラー\)](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)」ページにアクセスすると、拡張機能のバージョン履歴を参照できます。  
  
#### パッケージ マネージャーの GUI を使用した JSON Web トークン ハンドラーのダウンロード  
  
1.  Visual Studio の**ソリューション エクスプローラー**でプロジェクトを右クリックし、**\[NuGet パッケージの管理\]** を選択します。  
  
2.  **\[NuGet パッケージの管理\]** ウィンドウで、検索ボックスをクリックし、「`JWT Token Handler`」と入力して **Enter** キーを押します。  
  
3.  結果ペインから、最初の結果の **\[インストール\]** をクリックします。  
  
4.  パッケージのダウンロードが開始されます。  プロジェクトに追加される前に、\[License Acceptance\] ダイアログ ボックスが表示されます。  ライセンス条項に同意する場合は、**\[I Accept\]** をクリックします。  
  
5.  最新の JSON Web トークン ハンドラー アセンブリがダウンロードされ、プロジェクトに追加されます。  
  
#### パッケージ マネージャー コンソールを使用した JSON Web トークン ハンドラーのダウンロード  
  
1.  Visual Studio で、**\[ツール\]**、**\[ライブラリ パッケージ マネージャー\]**、**\[パッケージ マネージャー コンソール\]** の順にクリックします。  
  
2.  **\[パッケージ マネージャー コンソール\]** が表示されます。  次のテキストを入力し、**Enter** キーを押します。  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  最新の JSON Web トークン ハンドラー アセンブリがダウンロードされ、プロジェクトに追加されます。