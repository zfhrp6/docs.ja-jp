---
title: "プリンシパル オブジェクトの置き換え | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "プリンシパル オブジェクト, 置換"
  - "セキュリティ [.NET Framework], プリンシパル"
  - "セキュリティ [.NET Framework], 置き換え (プリンシパル オブジェクトを)"
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# プリンシパル オブジェクトの置き換え
認証サービスを提供するアプリケーションでは、特定のスレッドの**プリンシパル** オブジェクト \(<xref:System.Security.Principal.IPrincipal>\) を置換する必要があります。 さらに、虚偽の ID やロールを要求することにより、悪意をもってアタッチされた不適切な**プリンシパル**がアプリケーションのセキュリティに問題を生じさせるため、セキュリティ システムを活用して**プリンシパル** オブジェクトを置き換える機能を保護する必要があります。 そのため、**プリンシパル** オブジェクトを置き換える機能を必要とするアプリケーションに、プリンシパルを制御するための <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName> オブジェクトを付与する必要があります。 \(ロール ベースのセキュリティ チェックを実行する、または**プリンシパル** オブジェクトを作成するために、このアクセス許可は必要がないことに注意してください。\)  
  
 次のタスクを実行することによって、現在の**プリンシパル** オブジェクトを置き換えることができます。  
  
1.  置き換える**プリンシパル** オブジェクトと関連付けられている **ID** オブジェクトを作成します。  
  
2.  新しい**プリンシパル** オブジェクトを呼び出しコンテキストにアタッチします。  
  
## 例  
 次の例では、汎用プリンシパル オブジェクトを作成し、それを使用してスレッドのプリンシパルを設定する方法を示します。  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## 参照  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName>   
 [プリンシパル オブジェクトと ID オブジェクト](../../../docs/standard/security/principal-and-identity-objects.md)