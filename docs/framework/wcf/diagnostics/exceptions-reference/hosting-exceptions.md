---
title: "ホスティング例外"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cfbe5fa9944b97704f153e9b38229ddfd28a9c5d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="hosting-exceptions"></a>ホスティング例外
ここでは、ホスティングによって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|完全 URI は許可されていません。 完全 URI は、ServiceHostingEnvironment.EnsureServiceAvailable API に対しては許可されていません。 対応するサービスの仮想パスを使用してください。|  
|Hosting_BuildProviderCouldNotCreateType|指定した CLR 型をサービスのコンパイル中に読み込むことができません。 この型がいずれか、アプリケーションのあるソース ファイルで定義されていることを確認\\\App_Code ディレクトリ、コンパイルされたアセンブリをアプリケーションの配置に含まれている\\\bin ディレクトリ、またはにインストールされているアセンブリ内に存在しますグローバル アセンブリ キャッシュします。 型名では、大文字と小文字が区別されます。 などのディレクトリ\\\App_Code と\\\bin は、アプリケーションのルート ディレクトリに置く必要があります。 \\\App_Code と\\\bin ディレクトリをサブディレクトリで入れ子にすることはできません。|
