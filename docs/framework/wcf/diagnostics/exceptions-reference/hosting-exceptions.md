---
title: ホスティング例外
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: f2bc7d0ca09faa2598990437295d1abf0cff3c45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33469438"
---
# <a name="hosting-exceptions"></a>ホスティング例外
ここでは、ホスティングによって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|完全 URI は許可されていません。 完全 URI は、ServiceHostingEnvironment.EnsureServiceAvailable API に対しては許可されていません。 対応するサービスの仮想パスを使用してください。|  
|Hosting_BuildProviderCouldNotCreateType|指定した CLR 型をサービスのコンパイル中に読み込むことができません。 この型がいずれか、アプリケーションのあるソース ファイルで定義されていることを確認\\\App_Code ディレクトリ、コンパイルされたアセンブリをアプリケーションの配置に含まれている\\\bin ディレクトリ、またはにインストールされているアセンブリ内に存在しますグローバル アセンブリ キャッシュします。 型名では、大文字と小文字が区別されます。 などのディレクトリ\\\App_Code と\\\bin は、アプリケーションのルート ディレクトリに置く必要があります。 \\\App_Code と\\\bin ディレクトリをサブディレクトリで入れ子にすることはできません。|
