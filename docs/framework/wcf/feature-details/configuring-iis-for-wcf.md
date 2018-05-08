---
title: Windows Communication Foundation での Internet Information Services 7.0 の構成
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 3e34f46fbf3ccf12c6a89a7cac96143965d958d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Windows Communication Foundation での Internet Information Services 7.0 の構成
Internet Information Services (IIS) 7.0 はモジュール設計になっており、必要なコンポーネントを選択してインストールできます。 この設計は、[!INCLUDE[wv](../../../../includes/wv-md.md)] で新しく導入されたマニフェスト ドリブンのコンポーネント テクノロジに基づいています。 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] には、40 以上のスタンドアロン機能コンポーネントがあり、個別にインストールできます。 これにより、IT プロフェッショナルは必要に応じてインストールをカスタマイズできます。 このトピックで構成する方法について説明します[!INCLUDE[iisver](../../../../includes/iisver-md.md)]の Windows Communication Foundation (WCF) を使用し、必要なコンポーネントを決定します。  
  
## <a name="minimal-installation-installing-was"></a>最小インストール : WAS のインストール  
 完全な [!INCLUDE[iisver](../../../../includes/iisver-md.md)] パッケージの最小インストールでは、Windows プロセス アクティブ化サービス (WAS: Windows Process Activation Service) をインストールします。 WAS はスタンドアロン機能であり、すべての [!INCLUDE[iisver](../../../../includes/iisver-md.md)] オペレーティング システム (Home Basic、Home Premium、Business、Ultimate、および Enterprise) で利用できる唯一の [!INCLUDE[wv](../../../../includes/wv-md.md)] の機能です。  
  
 コントロール パネル からをクリックして**プログラム** をクリックし、 **Windows の機能のオンまたはオフ**の下に表示される**プログラムと機能**に WAS コンポーネントが表示、次の図のようにリストします。  
  
 ![切り替える機能をオフ ダイアログ](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")  
  
 この機能には、次のサブコンポーネントがあります。  
  
-   .NET 環境  
  
-   構成 API  
  
-   プロセス モデル  
  
 WAS のルート ノードのみを選択するかどうか、**プロセス モデル**サブ ノードは既定でオンにします。 このインストールでは Web サーバーをサポートしないため、WAS のみをインストールすることに注意してください。  
  
 WCF またはいずれかに[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]するために、アプリケーションを確認して、 **.NET 環境**チェック ボックスをオンします。 つまり、すべての WAS コンポーネントは WCF のために必要と[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]を適切に機能します。 これらのコンポーネントのいずれかを一度インストールすると、チェック ボックスは自動的にオンになります。  
  
## <a name="iis-70-default-installation"></a>IIS 7.0 : 既定のインストール  
 チェックして、**インターネット インフォメーション サービス**サブ ノードの一部の機能は、次の図に示すように自動的にチェックします。  
  
 ![IIS 7.0 の機能の既定の設定](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")  
  
 これは [!INCLUDE[iisver](../../../../includes/iisver-md.md)] の既定のインストールです。 このインストールにより、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] を使用して静的コンテンツ (HTML ページなど) を提供できます。 ただし、実行することはできません[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]または CGI アプリケーションまたは WCF サービスをホストします。  
  
## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7.0 : ASP.NET サポートを行うインストール  
 IIS 7.0 で [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] を機能させるには [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] をインストールする必要があります。 チェックした後**ASP.NET**画面に、次の図のようになります。  
  
 ![Asp.NET の設定に必要な](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")  
  
 これは、両方の WCF の最低限の環境と[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]で動作するアプリケーション[!INCLUDE[iisver](../../../../includes/iisver-md.md)]です。  
  
## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7.0 : IIS 6.0 互換コンポーネントを備えたインストール  
 インストールするときに[!INCLUDE[iisver](../../../../includes/iisver-md.md)]Visual Studio 2005 または他の自動化スクリプトまたはを使用した仮想アプリケーションを構成する (Adsutil.vbs) などのツールがシステムの[!INCLUDE[iis601](../../../../includes/iis601-md.md)]メタベース API では、確認することを確認してください、 [!INCLUDE[iis601](../../../../includes/iis601-md.md)]  **。スクリプト ツール**です。 他のサブ ノードを自動的に確認[!INCLUDE[iis601](../../../../includes/iis601-md.md)]**互換性のある管理**です。 実行後の画面を次の図に示します。  
  
 ![IIS 6.0 管理互換の設定](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")  
  
 このインストールがあるを使用するために必要なすべて[!INCLUDE[iisver](../../../../includes/iisver-md.md)]、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]および WCF の機能とサンプルは、Web でご確認いただけます。  
  
## <a name="request-limits"></a>要求の制限  
 IIS 7.0 がインストールされた [!INCLUDE[wv](../../../../includes/wv-md.md)] では、`maxUri` および `maxQueryStringSize` の設定の既定値が変更されています。 既定では、IIS 7.0 における要求のフィルター処理で使用できる文字数は、URL が 4096 文字、クエリ文字列が 2048 文字です。 これらの既定値を変更するには、App.config ファイルに次の XML を追加します。  
  
 `<system.webServer>`  
  
 `<security>`  
  
 `<requestFiltering>`  
  
 `<requestLimits maxUrl="8192" maxQueryString="8192" />`  
  
 `</requestFiltering>`  
  
 `</security>`  
  
 `</system.webServer>`  
  
## <a name="see-also"></a>関連項目  
 [WAS アクティベーション アーキテクチャ](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [WCF で使用するための WAS を設定する](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [方法 : WCF アクティブ化コンポーネントをインストールして設定する](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [Windows Server App Fabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)
