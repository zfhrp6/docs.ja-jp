---
title: 'コア通信 : Webhost サポート'
ms.date: 03/30/2017
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
ms.openlocfilehash: 724dc2eb66d058920fda07af899cd7464182c438
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="core-communications-webhost-support"></a>コア通信 : Webhost サポート
ここでは、Webhost サポートによって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|Hosting_CompatibilityServiceNotHosted|このサービスでは、ASP.NET 互換性が必要です。 また、IIS でホストする必要もあります。 Web.config で ASP.NET 互換性を有効にして IIS でサービスをホストするか、または AspNetCompatibilityRequirementsAttribute.AspNetCompatibilityRequirementsMode プロパティを Required 以外の値に設定します。|  
|Hosting_ListenerNotFoundForActivationInRecycling|指定されたアドレスをアクティブにリッスンしているチャネルはありません。 アプリケーションがリサイクルされる場合、サービスは閉じられます。|  
|Hosting_NonHTTPInCompatibilityMode|ASP.NET 互換性でサポートされるプロトコルは HTTP と HTTPS のみです。 指定されたエンドポイントを削除するか、アプリケーションに対して ASP.NET 互換性を無効にします。|  
|Hosting_ProcessNotExecutingUnderHostedContext|指定されたホスト プロセスは、現在のホスト環境内で呼び出すことができません。 この API では、アプリケーションの呼び出しがインターネット インフォメーション サービスまたは Windows プロセス アクティブ化サービス内で干すとされている必要があります。|  
|Hosting_ServiceCompatibilityRequire|このサービスは ASP.NET 互換性を必要とするため、アクティブにできません。 このアプリケーションに対して、ASP.NET 互換性が有効になっていません。 Web.config ファイルで ASP.NET 互換性を有効にするか、AspNetCompatibilityRequirementsAttribute.AspNetCompatibilit を設定します。|
