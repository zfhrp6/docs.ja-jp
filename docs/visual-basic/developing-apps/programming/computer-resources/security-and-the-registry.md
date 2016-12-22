---
title: "Security and the Registry (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "security [Visual Basic], registry"
  - "registry, security issues"
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Security and the Registry (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

このページでは、レジストリにデータを格納する際のセキュリティに関連する事項について説明します。  
  
## アクセス許可  
 レジストリ キーが ACL \(Access Control List\) によって保護されているとはいえ、パスワードなどの秘密のデータを書式なしテキストでレジストリに格納するのは危険です。  
  
 レジストリの作業には、システム リソースや保護情報などへの不適切なアクセスを許可する場合があるため、セキュリティが損なわれる場合があります。  これらのプロパティを使用するには、レジストリ変数へのアクセスを制御する、<xref:System.Security.Permissions.RegistryPermissionAccess> 列挙型の、読み取りアクセス許可および書き込みアクセス許可を持っている必要があります。  完全に信頼された状態で実行中のコード \(既定のセキュリティ ポリシーでは、ユーザーのローカル ハードディスクにインストールされているすべてのコード\) は、レジストリにアクセスするために必要なアクセス許可を持っています。  詳細については、<xref:System.Security.Permissions.RegistryPermission> クラスのトピックを参照してください。  
  
 レジストリ変数は、<xref:System.Security.Permissions.RegistryPermission> を持たないコードがアクセスできるメモリ位置に格納することはできません。  同様に、アクセス許可が付与されるとき、作業を行うために必要な最小限の権限が付与されます。  
  
 レジストリ アクセス許可のアクセス値は、<xref:System.Security.Permissions.RegistryPermissionAccess> 列挙型で定義します。  各メンバーを次の表に示します。  
  
|値|レジストリ変数へのアクセス|  
|-------|-------------------|  
|`AllAccess`|作成、読み取り、書き込み|  
|`Create`|Create|  
|`NoAccess`|アクセスなし|  
|`Read`|Read|  
|`Write`|Write|  
  
## レジストリ キーの値のチェック  
 レジストリの値を作成するときは、その値が既存の値である場合の処理を決めておく必要があります。  悪意のあるユーザーによって作成された別のプロセスが既に値を作成し、アクセス権を持っている可能性があります。  レジストリ値にデータを設定すると、そのデータを他のプロセスから利用できるようになります。  これを回避するために、`GetValue` メソッドを使用します。  このメソッドは、キーがまだ存在しない場合、`Nothing` を返します。  
  
> [!IMPORTANT]
>  Web アプリケーションからレジストリを読み取る場合、現在のユーザーの ID は、Web アプリケーションで実装されている認証と偽装によって異なります。  
  
## 参照  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 [Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)