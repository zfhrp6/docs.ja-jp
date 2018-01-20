---
title: "アセンブリ バインディング リダイレクトのセキュリティ アクセス許可"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d2593df04b93db17f9ca61a98b21aaec1d534d46
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="assembly-binding-redirection-security-permission"></a>アセンブリ バインディング リダイレクトのセキュリティ アクセス許可
アプリケーション構成ファイルで明示的にアセンブリ バインディングをリダイレクトするには、セキュリティ アクセス許可が必要です。 これは、.NET Framework アセンブリおよびサードパーティ製アセンブリに適用されます。 許可を設定して、<xref:System.Security.Permissions.SecurityPermissionFlag>フラグを<xref:System.Security.Permissions.SecurityPermission>です。 マネージ アセンブリは、既定ではアクセス許可を持っていません。  
  
 セキュリティ アクセス許可は、信頼済みゾーン (ローカル コンピューター) とイントラネット ゾーンで実行されているアプリケーションに与えられます。 インターネット ゾーンで実行されているアプリケーションが禁止アセンブリ バインド リダイレクトを実行します。  
  
 コンポーネントの発行者によって制御されるパブリッシャー ポリシー ファイル、または管理者によって制御されるコンピューターの構成ファイルでアセンブリのリダイレクトを実行する場合は、アクセス許可は必要ありません。 ただし、アクセス許可は、アプリケーションを使用して発行者ポリシーを明示的に無視する必要が、 [ \<publisherPolicy 適用 ="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)アプリケーション構成ファイル内の要素。  
  
 次の表は、既定のセキュリティ設定、**すること**フラグ。  
  
|ゾーン|設定することフラグ|  
|----------|-----------------------------------|  
|信頼済みゾーン (ローカル コンピューター)|**ON**|  
|イントラネット ゾーン|**ON**|  
|インターネット ゾーン|**OFF**|  
|信頼されていないゾーン|**OFF**|  
  
 管理者は、これらのセキュリティ設定をサポートしたり、特定のコンピューターで特定のシナリオの制限を変更できます。 変更するためのツールがない、**すること**フラグです。 既定値の設定、管理者はユーザーのコンピューターに Security.config ファイルを編集してする必要があります手動でします。  
  
## <a name="see-also"></a>参照  
 [発行者ポリシー ファイルとサイド バイ サイド実行](http://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [方法: 自動バインディング リダイレクトを有効/無効にする](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [side-by-side 実行](../../../docs/framework/deployment/side-by-side-execution.md)
