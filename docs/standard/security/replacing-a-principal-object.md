---
title: "プリンシパル オブジェクトの置き換え"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c53064ae12889df09b5259fbb7c8159cfdcd07aa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="replacing-a-principal-object"></a>プリンシパル オブジェクトの置き換え
認証サービスを提供するアプリケーションでは、特定のスレッドの **プリンシパル** オブジェクト (<xref:System.Security.Principal.IPrincipal>) を置換する必要があります。 さらに、虚偽の ID やロールを要求することにより、悪意をもってアタッチされた不適切な **プリンシパル** がアプリケーションのセキュリティに問題を生じさせるため、セキュリティ システムを活用して **プリンシパル** オブジェクトを置き換える機能を保護する必要があります。 そのため、アプリケーションを必要とするを置き換える機能**プリンシパル**オブジェクトを付与する必要があります、<xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>プリンシパル コントロールのオブジェクト。 (ロール ベースのセキュリティ チェックを実行する、または **プリンシパル** オブジェクトを作成するために、このアクセス許可は必要がないことに注意してください。)  
  
 次のタスクを実行することによって、現在の **プリンシパル** オブジェクトを置き換えることができます。  
  
1.  置き換える **プリンシパル** オブジェクトと関連付けられている **ID** オブジェクトを作成します。  
  
2.  新しい **プリンシパル** オブジェクトを呼び出しコンテキストにアタッチします。  
  
## <a name="example"></a>例  
 次の例では、汎用プリンシパル オブジェクトを作成し、それを使用してスレッドのプリンシパルを設定する方法を示します。  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
 [プリンシパル オブジェクトと ID オブジェクト](../../../docs/standard/security/principal-and-identity-objects.md)
