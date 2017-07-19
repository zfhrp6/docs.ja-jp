---
title: "Windows Communication Foundation での Internet Information Services 7.0 の構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Windows Communication Foundation での Internet Information Services 7.0 の構成
Internet Information Services \(IIS\) 7.0 はモジュール設計になっており、必要なコンポーネントを選択してインストールできます。この設計は、[!INCLUDE[wv](../../../../includes/wv-md.md)] で新しく導入されたマニフェスト ドリブンのコンポーネント テクノロジに基づいています。[!INCLUDE[iisver](../../../../includes/iisver-md.md)] には、40 以上のスタンドアロン機能コンポーネントがあり、個別にインストールできます。これにより、IT プロフェッショナルは必要に応じてインストールをカスタマイズできます。このトピックでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] で使用する [!INCLUDE[iisver](../../../../includes/iisver-md.md)] を構成し、必要なコンポーネントを決定する方法について説明します。  
  
## 最小インストール : WAS のインストール  
 完全な [!INCLUDE[iisver](../../../../includes/iisver-md.md)] パッケージの最小インストールでは、Windows プロセス アクティブ化サービス \(WAS: Windows Process Activation Service\) をインストールします。WAS はスタンドアロン機能であり、すべての [!INCLUDE[wv](../../../../includes/wv-md.md)] オペレーティング システム \(Home Basic、Home Premium、Business、Ultimate、および Enterprise\) で利用できる唯一の [!INCLUDE[iisver](../../../../includes/iisver-md.md)] の機能です。  
  
 コントロール パネルの **\[プログラム\]** をクリックし、**\[プログラムと機能\]** に表示される **\[Windows の機能を有効化または無効化\]** をクリックします。次の図に示すように、一覧に WAS コンポーネントが表示されます。  
  
 ![機能の有効化または無効化ダイアログ](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc\_TurnFeaturesOnOrOffs")  
  
 この機能には、次のサブコンポーネントがあります。  
  
-   .NET 環境  
  
-   構成 API  
  
-   プロセス モデル  
  
 WAS のルート ノードを選択した場合は、既定で **\[プロセス モデル\]** サブノードだけがオンになっています。このインストールでは Web サーバーをサポートしないため、WAS のみをインストールすることに注意してください。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] または任意の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションを機能させるには、**\[.NET 環境\]** チェック ボックスをオンにします。つまり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] および [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] を適切に機能させるには、すべての WAS コンポーネントが必要です。これらのコンポーネントのいずれかを一度インストールすると、チェック ボックスは自動的にオンになります。  
  
## IIS 7.0 : 既定のインストール  
 **\[インターネット インフォメーション サービス\]** 機能をオンにすることで、次の図に示すように、一部のサブノードが自動的にオンになります。  
  
 ![IIS 7.0 の各機能の既定の設定](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc\_TurningFeaturesOnOrOff2")  
  
 これは [!INCLUDE[iisver](../../../../includes/iisver-md.md)] の既定のインストールです。このインストールにより、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] を使用して静的コンテンツ \(HTML ページなど\) を提供できます。ただし、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] や CGI アプリケーションを実行したり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストしたりすることはできません。  
  
## IIS 7.0 : ASP.NET サポートを行うインストール  
 IIS 7.0 で [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] を機能させるには [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] をインストールする必要があります。**\[ASP.NET\]** をオンにすると、画面は次のようになります。  
  
 ![ASP.NET の必須の設定](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc\_TrunFeaturesOnOrOFf3s")  
  
 これは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションと [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションの両方が [!INCLUDE[iisver](../../../../includes/iisver-md.md)] で機能するための最小限の環境です。  
  
## IIS 7.0 : IIS 6.0 互換コンポーネントを備えたインストール  
 Visual Studio 2005 や、[!INCLUDE[iis601](../../../../includes/iis601-md.md)] メタベース API を使用する仮想アプリケーションを構成するオートメーション スクリプトおよびツール \(Adsutil.vbs など\) と共にシステムに [!INCLUDE[iisver](../../../../includes/iisver-md.md)] をインストールする場合は、**\[[!INCLUDE[iis601](../../../../includes/iis601-md.md)] スクリプト ツール\]** を必ずオンにしてください。これにより、**\[[!INCLUDE[iis601](../../../../includes/iis601-md.md)] Management 互換性\]** の他のサブノードが自動的にオンになります。実行後の画面を次の図に示します。  
  
 ![IIS 6.0 管理互換の設定](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc\_TurnFeaturesOnOrOff5s")  
  
 このインストールにより、[!INCLUDE[iisver](../../../../includes/iisver-md.md)]、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]、および [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 機能を使用するために必要な準備ができ、Web でサンプルを利用できるようになります。  
  
## 要求の制限  
 IIS 7.0 がインストールされた [!INCLUDE[wv](../../../../includes/wv-md.md)] では、`maxUri` および `maxQueryStringSize` の設定の既定値が変更されています。既定では、IIS 7.0 における要求のフィルター処理で使用できる文字数は、URL が 4096 文字、クエリ文字列が 2048 文字です。これらの既定値を変更するには、App.config ファイルに次の XML を追加します。  
  
 `<system.webServer>`  
  
 `<security>`  
  
 `<requestFiltering>`  
  
 `<requestLimits maxUrl=”8192” maxQueryString=”8192” />`  
  
 `</requestFiltering>`  
  
 `</security>`  
  
 `</system.webServer>`  
  
## 参照  
 [WAS アクティベーション アーキテクチャ](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)   
 [WCF で使用するための WAS を設定する](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)   
 [方法 : WCF アクティブ化コンポーネントをインストールして設定する](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)   
 [AppFabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)