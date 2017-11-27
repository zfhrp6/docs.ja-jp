---
title: "COM アプリケーションとの統合の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4e995fc66a925cb0ebe272c9dceca1ba63b9459d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="integrating-with-com-applications-overview"></a>COM アプリケーションとの統合の概要
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、マネージ コード開発者は、接続されたアプリケーションを作成するための多彩な環境を使用できます。 ただし、COM ベースのアンマネージ コードにかなりの投資を行っており移行を望まない場合でも、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス モニカーを使用することで、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web サービスを既存のコードに直接統合できます。 サービス モニカーは Office VBA、Visual Basic 6.0、または Visual C++ 6.0 などの幅広い COM ベースの開発環境で使用可能です。  
  
> [!NOTE]
>  サービス モニカーは、すべての通信に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の通信チャネルを使用します。 このチャネルのセキュリティ メカニズムと識別メカニズムは、標準の COM および DCOM プロキシで使用されるものとは異なります。 また、サービス モニカーでは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の通信チャネルを使用するため、すべての呼び出しの既定のタイムアウト時間が 1 分になります。  
  
 サービス モニカーを `GetObject` 関数と共に使用することで、アンマネージ開発者は、厳密に型指定された COM 固有の方法を使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web サービスを呼び出すことができます。 そのためには、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web サービス コントラクトの定義と、使用されるバインディングが、ローカル COM から参照できる必要があります。 他の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントの場合と同様に、サービス モニカーではサービスへの型指定されたチャネルを構築する必要がありますが、このチャネルは、最初のメソッド呼び出し時に COM プログラマには透過的に構築されます。  
  
 他の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントと同じように、アプリケーションはモニカーを使用する際に、サービスとの通信に使用するアドレス、バインディング、およびコントラクトを指定します。 コントラクトは、次のいずれかの方法で指定できます。  
  
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
>  完全に COM ベースのクライアントと共にサービス モニカーを使用する場合でも、クライアント コンピューターには [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] とこれをサポートする .NET Framework 2.0 がインストールされている必要があります。 また、サービス モニカーを使用するクライアント アプリケーションには、適切なバージョンの .NET Framework ランタイムが読み込まれていることが重要です。 Office アプリケーション内でモニカーを使用する場合、構成ファイルに、正しいフレームワーク バージョンが読み込まれていることを確認する必要があります。 たとえば Excel の場合、Excel.exe ファイルと同じディレクトリにある Excel.exe.config というファイルに、次のテキストが記述されている必要があります。  
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
 [方法: 登録し、サービス モニカーの構成](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
