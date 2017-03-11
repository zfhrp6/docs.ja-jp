---
title: "How to: Delete a Registry Key in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.DeleteSetting"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "GetSetting function"
  - "registry, deleting values"
  - "GetAllSettings function"
  - "registry keys, deleting"
  - "registry, deleting keys"
  - "examples [Visual Basic], registry"
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
caps.latest.revision: 28
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 28
---
# How to: Delete a Registry Key in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> メソッドおよび <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> メソッドを使用して、レジストリ キーを削除できます。  
  
## 手順  
  
#### レジストリ キーを削除するには  
  
-   `DeleteSubKey` メソッドを使用して、レジストリ キーを削除します。  この例では、CurrentUser ハイブの Software\/TestApp キーを削除します。  これは、コード内で適切な文字列に変更できます。または、ユーザーが指定した情報を使用できます。  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/how-to-delete-a-registry_1.vb)]  
  
## 信頼性の高いプログラミング  
 キーと値の組み合わせが存在しない場合、`DeleteSubKey` メソッドは空の文字列を返します。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   キーの名前が `Nothing` \(<xref:System.ArgumentNullException>\) である場合。  
  
-   レジストリ キーを削除するためのアクセス許可がユーザーにない場合 \(<xref:System.Security.SecurityException>\)  
  
-   キー名が 255 文字の制限を超えている場合 \(<xref:System.ArgumentException>\)  
  
-   レジストリ キーが読み取り専用の場合 \(<xref:System.UnauthorizedAccessException>\)  
  
## .NET Framework セキュリティ  
 必要なアクセス許可が実行時に与えられない \(<xref:System.Security.Permissions.RegistryPermission>\) 場合、またはユーザーが設定の作成や書き込みを行うための適切な \(ACL によって決定された\) アクセス権を持っていない場合、レジストリ呼び出しは失敗します。  たとえば、コード アクセス セキュリティ権限のあるローカル アプリケーションに、オペレーティング システム権限があるとは限りません。  
  
## 参照  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>   
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>   
 <xref:Microsoft.Win32.RegistryKey>   
 [Security and the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)   
 [Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)