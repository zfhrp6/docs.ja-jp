---
title: Identity and Access Tool for Visual Studio 2012
ms.date: 03/30/2017
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 107028b89d576b27a2559fd0ae5298c849da2c94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398610"
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a>Identity and Access Tool for Visual Studio 2012
このトピックでは、新しい Identity and Access Tool for Visual Studio 11 について説明します。 このツールは、次の URL からダウンロードできます: [ http://go.microsoft.com/fwlink/?LinkID=245849 ](http://go.microsoft.com/fwlink/?LinkID=245849)またはから直接、拡張機能マネージャーで直接には、"identity"を検索して Visual Studio 11 内です。  
  
 Identity and Access Tool for Visual Studio 11 の特長を次に示します。これにより、開発時の操作性が大幅に簡素化されます。  
  
-   新しいツールを使用すると、Web アプリケーション プロジェクトの種類およびターゲット IIS Express を使用して開発できます。  
  
-   ブランケット保護のみの認証とは異なり、新しいツールによって、ローカルのホーム レルム探索ページ/コントローラー (または、アプリケーション内で認証によって実行されるその他のエンドポイント処理) を指定できます。WIF は要求の構成を変更して、認証されていないすべての要求が、STS ではなくその場所にリダイレクトされるようにします。  
  
-   ツールには、テスト セキュリティ トークン サービス (STS) が含まれています。この STS は、デバッグ セッションの起動時にローカル コンピューターで実行されます。 したがって、アプリケーションのテストに必要なクレームを取得する目的で、カスタム STS プロジェクトを作成して調整する必要はありません。 クレームの種類と値は完全にカスタマイズできます。  
  
-   ツールの UI を使用して共通の設定を直接変更できます。web.config を編集する必要はありません。  
  
-   Active Directory フェデレーション サービス (AD FS) 2.0 (または、他の WS-Federation プロバイダー) を使用して、1 つの画面でフェデレーションを確立できます。  
  
-   ツールでは Microsoft Azure のアクセス制御サービス (ACS) の機能を使用できます。この機能には、使用するすべての ID プロバイダー (Facebook、Google、Live ID、Yahoo! などの OpenID プロバイダー、および WS-Federation プロバイダー) のチェック ボックスが用意されています。 ID プロバイダーのチェック ボックスをオンにして、[OK] をクリックし、F5 キーを押すと、アプリケーションと ACS の両方が自動的に構成され、テスト アプリケーションが ACS 対応になります。  
  
## <a name="see-also"></a>関連項目  
 [WIF の機能](../../../docs/framework/security/wif-features.md)
