---
title: "Reading from and Writing to the Registry (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Computer.Registry object, tasks"
  - "registry, writing to"
  - "registry, reading"
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Reading from and Writing to the Registry (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このトピックではレジストリに関連する概念説明のトピックとタスクについて説明します。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のプログラミングでは、レジストリへのアクセスには、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] に用意されている関数を使用する方法と、.NET Framework のレジストリ クラスを使用する方法のいずれかを選択できます。  レジストリは、オペレーティング システムによる情報と、コンピューターにホストされるアプリケーションによる情報をホストします。  レジストリの作業には、システム リソースや保護情報などへの不適切なアクセスを許可する場合があるため、セキュリティが損なわれる場合があります。  
  
## このセクションの内容  
 [How to: Create a Registry Key and Set Its Value](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 `My.Computer.Registry` のオブジェクトの `CreateSubKey` と `SetValue` のメソッドをレジストリ キーを作成し値を設定する方法について説明します。  
  
 [How to: Read a Value from a Registry Key](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 `My.Computer.Registry` オブジェクトのメソッドを `GetValue` のレジストリ キーの値を読み取るために使用する方法について説明します。  
  
 [How to: Delete a Registry Key](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 `My.Computer.Registry.CurrentUser` のプロパティのメソッドを `DeleteSubKey` のレジストリ キーを削除する方法について説明します。  
  
 [Microsoft.Win32 名前空間を使用したレジストリの読み取りと書き込み](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] の `Registry` と `RegistryKey` のクラスを使用してレジストリにアクセスする方法について説明します。  
  
 [Security and the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 レジストリに関連するセキュリティ問題について説明します。  
  
## 関連項目  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 `My.Computer.Registry` オブジェクトのメンバーを一覧表示し、説明します。  
  
 <xref:Microsoft.Win32.Registry>  
 `Registry` クラスの概要を説明します。個々のキーとメンバーへのリンクが用意されています。