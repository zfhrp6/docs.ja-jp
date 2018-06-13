---
title: COM アプリケーションとの統合の概要
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: c789d4a52da9b2785fb5919a674bf19f23d23509
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493397"
---
# <a name="integrating-with-com-applications-overview"></a>COM アプリケーションとの統合の概要
Windows Communication Foundation (WCF) では、マネージ コードを開発者に接続されているアプリケーションを作成するための有用な環境を提供します。 ただし、アンマネージの COM ベースのコードにかなりの投資があるして移行したくない場合も統合できます WCF Web サービス、既存のコードに直接 WCF サービス モニカーを使用しています。 サービス モニカーは Office VBA、Visual Basic 6.0、または Visual C++ 6.0 などの幅広い COM ベースの開発環境で使用可能です。  
  
> [!NOTE]
>  サービス モニカーでは、すべての通信を WCF 通信チャネルを使用します。 このチャネルのセキュリティ メカニズムと識別メカニズムは、標準の COM および DCOM プロキシで使用されるものとは異なります。 さらに、サービス モニカーは既定のタイムアウト期間の WCF 通信チャネルを使用しているために、1 分間のすべての呼び出しです。  
  
 サービス モニカーを使用、 `GetObject` WCF Web サービスを呼び出すため、厳密に型指定された COM 固有のアプローチをアンマネージ開発者に提供する関数。 これには、ローカルの WCF Web サービスのコントラクトとバインディングを使用している COM 参照の定義が必要です。 他の WCF クライアントと同様にこのコンストラクションはチャネルは透過的に COM プログラマに最初のメソッド呼び出しに、サービス モニカーは、サービスに型指定されたチャネルを作成する必要があります。  
  
 他の WCF クライアントが、モニカーを使用する場合、共通のアプリケーションは、アドレス、バインディング、およびサービスと通信するためのコントラクトを指定します。 コントラクトは、次のいずれかの方法で指定できます。  
  
-   型指定のあるコントラクト - クライアント コンピューターで COM から参照できる型として登録されます。  
  
-   WSDL コントラクト - WSDL ドキュメントという形で供給されます。  
  
-   MEX コントラクト - 実行時に Metadata Exchange (MEX) エンドポイントから取得されます。  
  
## <a name="parameters-supported-by-the-service-moniker"></a>サービス モニカーでサポートされるパラメーター  
 サービス モニカーでサポートされるパラメーターを次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`address`|サービスの URL 位置。|  
|`binding`|アプリケーション構成のバインディング セクションの名前。|  
|`bindingConfiguration`|名前付きバインディング セクション内の名前付きバインディング インスタンス。|  
|`contract`|サービス コントラクトまたは (MEX の) コントラクト名を表すインターフェイス識別子 (IID)。|  
|`wsdl`|代替形式のコントラクト定義を提供する WSDL ドキュメント。|  
|`spnIdentity`|サービスとの通信に使用するサーバー プリンシパル名 (SPN) ID。|  
|`upnIdentity`|サービスとの通信に使用するユーザー プリンシパル名 (UPN) ID。|  
|`dnsIdentity`|サービスとの通信に使用する DNS ID。|  
|`mexAddress`|サービスの Metadata Exchange (MEX) エンドポイントの URL 位置。|  
|`mexBinding`|MEX エンドポイントと接続するための、アプリケーション構成のバインディング セクションの名前。|  
|`mexBindingConfiguration`|MEX エンドポイントと接続する名前付きバインディング セクション内の名前付きバインディング インスタンス。|  
|`bindingNamespace`|取得する MEX のバインディング セクション名の名前空間。|  
|`contractNamespace`|取得する MEX のコントラクトの名前空間。|  
|`mexSpnIdentity`|MEX エンドポイントとの通信に使用するサーバー プリンシパル名 (SPN) ID。|  
|`mexUpnIdentity`|MEX エンドポイントとの通信に使用するユーザー プリンシパル名 (UPN) ID。|  
|`mexDnsIdentity`|MEX エンドポイントとの通信に使用する DNS ID。|  
|`serializer`|"XML" シリアライザーと "datacontract" シリアライザーのいずれを使用するかを指定します。|  
  
> [!NOTE]
>  すべての COM ベースのクライアントに使用する場合でも、クライアント コンピューターにインストールするには、WCF とサポートの .NET Framework 2.0 サービス モニカーが必要です。 また、サービス モニカーを使用するクライアント アプリケーションには、適切なバージョンの .NET Framework ランタイムが読み込まれていることが重要です。 Office アプリケーション内でモニカーを使用する場合、構成ファイルに、正しいフレームワーク バージョンが読み込まれていることを確認する必要があります。 たとえば Excel の場合、Excel.exe ファイルと同じディレクトリにある Excel.exe.config というファイルに、次のテキストが記述されている必要があります。  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  `<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a>関連項目  
 [方法 : サービス モニカーを登録および構成する](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
