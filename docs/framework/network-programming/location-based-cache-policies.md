---
title: "場所ベースのキャッシュ ポリシー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7a1be9f377f9b241bf46ac67f4f3f08fc5a43821
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="location-based-cache-policies"></a>場所ベースのキャッシュ ポリシー
場所ベースのキャッシュ ポリシーでは、要求されたリソースを取得できる場所に基づいて、有効なキャッシュされたエントリの鮮度を定義します。 キャッシュされたリソースを使用しても、サーバーに指定されている再検証要件に違反しない場合、キャッシュされたリソースは有効です。 場所ベースのキャッシュ ポリシーをプログラムで作成するには、<xref:System.Net.Cache.RequestCachePolicy> または <xref:System.Net.Cache.HttpRequestCachePolicy> クラス コンストラクターを使用します。 場所ベースのポリシーの種類は、<xref:System.Net.Cache.RequestCacheLevel> または <xref:System.Net.Cache.HttpRequestCacheLevel> 列挙値を使用してコンストラクターに渡されます。 場所ベースのキャッシュ ポリシーを作成するコード例については、「[How to: Set a Location-Based Cache Policy for an Application](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md)」(方法: アプリケーションの場所ベースのキャッシュ ポリシーを設定する) を参照してください。 以下のセクションでは、ハイパーテキスト転送プロトコル (http と https) リソースに使用できる各種の場所ベースのキャッシュ ポリシーを定義します。  
  
## <a name="cache-if-available-policy"></a>"利用可能ならキャッシュを使用" ポリシー  
 有効な要求されたリソースがローカル キャッシュ内にある場合、キャッシュされたリソースが使用されます。それ以外の場合、そのリソースの要求はサーバーに送信されます。 要求されたリソースがクライアントとサーバーの間の何らかのキャッシュ内にある場合、中間のキャッシュが要求を満たすことができます。  
  
## <a name="cache-only-policy"></a>"キャッシュのみを使用" ポリシー  
 有効な要求されたリソースがローカル キャッシュ内にある場合、キャッシュされたリソースが使用されます。 このキャッシュ ポリシー レベルが指定された場合、項目がローカル キャッシュ内にない場合は <xref:System.Net.WebException> 例外がスローされます。  
  
## <a name="cache-or-next-cache-only-policy"></a>"キャッシュまたは次のキャッシュのみを使用" ポリシー  
 有効な要求されたリソースがローカル キャッシュ内にあるか、ローカル エリア ネットワーク上の中間キャッシュ内にある場合、キャッシュされたリソースが使用されます。 このような操作を行わない場合、<xref:System.Net.WebException> 例外がスローされます。 HTTP キャッシュ プロトコルの場合、only-if-cached キャッシュ コントロール ディレクティブを使用してこの処理が実行されます。  
  
## <a name="no-cache-no-store-policy"></a>"キャッシュを使用せず格納しない" ポリシー  
 要求されたリソースはキャッシュ内からは使用されず、キャッシュには格納されません。 要求されたリソースがローカル キャッシュ内にある場合は削除されます。 このポリシー レベルは、リソースの削除も必要な中間キャッシュに指定します。 HTTP キャッシュ プロトコルの場合、no-store キャッシュ コントロール ディレクティブを使用してこの処理が実行されます。  
  
## <a name="refresh-policy"></a>更新ポリシー  
 要求されたリソースがサーバーから取得された場合、またはローカル キャッシュ以外のキャッシュで見つかった場合、その要求されたリソースを使用できます。 中間キャッシュが要求を満たす前に、そのキャッシュは、サーバーに対してキャッシュされたエントリの再検証を行う必要があります。 HTTP キャッシュ プロトコルの場合、max-age = 0 キャッシュ コントロール ディレクティブと、no-cache Pragma ヘッダーを使用してこの処理が実行されます。  
  
## <a name="reload-policy"></a>ポリシーの再読み込み  
 要求されたリソースは、サーバーから取得する必要があります。 リソースがローカル キャッシュに保存されている可能性があります。 HTTP キャッシュ プロトコルの場合、no-cache キャッシュ コントロール ディレクティブと、no-cache Pragma ヘッダーを使用してこの処理が実行されます。  
  
## <a name="revalidate-policy"></a>再検証ポリシー  
 キャッシュ内のリソースのコピーとサーバー上のコピーを比較します。 サーバー上のコピーが新しい場合は、要求を満たすために使用され、キャッシュ内のコピーは置き換えられます。 キャッシュ内のコピーがサーバー上のコピーと同じ場合、キャッシュされたコピーが使用されます。 HTTP キャッシュ プロトコルの場合、条件付き要求を使用してこの処理が実行されます。  
  
## <a name="see-also"></a>関連項目  
 [ネットワーク アプリケーションのキャッシュ管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [キャッシュ ポリシー](../../../docs/framework/network-programming/cache-policy.md)  
 [時間ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [ネットワーク アプリケーションでのキャッシュの構成](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [\<requestCaching> 要素 (ネットワーク設定)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
