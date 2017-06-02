---
title: "アセンブリ バインディング リダイレクトのセキュリティ アクセス許可 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "アセンブリ [.NET Framework], バインディングのリダイレクト"
  - "side-by-side 実行, アセンブリ バインディング リダイレクト"
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# アセンブリ バインディング リダイレクトのセキュリティ アクセス許可
アプリケーション構成ファイルで明示的にアセンブリ バインディングをリダイレクトするには、セキュリティ アクセス許可が必要です。  これは、.NET Framework アセンブリおよびサードパーティ製アセンブリに適用されます。  アクセス許可は、[SecurityPermission クラス](frlrfSystemSecurityPermissionsSecurityPermissionClassTopic)の [BindingRedirects](frlrfSystemSecurityPermissionsSecurityPermissionFlagClassTopic) フラグを設定することによって付与されます。  既定では、マネージ アセンブリにはアクセス許可が付与されていません。  
  
 セキュリティ アクセス許可は、Trusted ゾーン \(ローカル マシン\) および Intranet ゾーンで実行されているアプリケーションに付与されます。  Internet ゾーンで実行されているアプリケーションは、アセンブリ バインディングのリダイレクトの実行が禁止されています。  
  
 コンポーネントの発行者によって制御される発行者ポリシー ファイルまたは管理者によって制御されるマシン構成ファイルで実行されるアセンブリのリダイレクトには、アクセス許可は必要ありません。  ただし、明示的にアプリケーション構成ファイルの [\<publisherPolicy apply\= "いいえ」\/\>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) 要素を使用して発行者ポリシーを無視する、アクセス許可はアプリケーションに必要です。  
  
 **BindingRedirects** フラグの既定のセキュリティ設定を次の表に示します。  
  
|ゾーン|BindingRedirects フラグの設定|  
|---------|-----------------------------|  
|Trusted ゾーン \(ローカル マシン\)|**ON**|  
|Intranet ゾーン|**ON**|  
|Internet ゾーン|**OFF**|  
|Untrusted ゾーン|**OFF**|  
  
 管理者は、これらのセキュリティ設定を変更して、特定のコンピューターで特定のシナリオをサポートしたり、制限したりすることができます。  **BindingRedirects** フラグの設定を既定から変更するツールはありません。管理者はユーザーのコンピューターで Security.config ファイルを手動で編集する必要があります。  
  
## 参照  
 [Publisher Policy Files and Side\-by\-Side Execution](http://msdn.microsoft.com/ja-jp/97a042be-4d72-40c3-91c0-76fd36bdf133)   
 [方法: 自動バインディング リダイレクトを有効\/無効にする](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)   
 [side\-by\-side 実行](../../../docs/framework/deployment/side-by-side-execution.md)