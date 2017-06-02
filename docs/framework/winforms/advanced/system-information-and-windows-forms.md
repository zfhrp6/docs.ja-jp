---
title: "システム情報と Windows フォーム | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ドメイン名, 取得"
  - "システム情報 [Windows フォーム]"
  - "SystemInformation クラス [Windows フォーム]"
  - "ユーザー名, 取得"
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# システム情報と Windows フォーム
コードにおいて何らかの決定を行うために、アプリケーションが実行されているコンピューターに関する情報を収集することが必要になる場合があります。  たとえば、特定のネットワーク ドメインに接続されているときだけ適用できる機能があるとします。この場合は、ドメインを識別し、ドメインが存在しない場合は機能を無効にする方法が必要になります。  
  
 Windows フォーム アプリケーションは、<xref:System.Windows.Forms.SystemInformation> クラスを使用して、実行時にコンピューターに関する各種の情報を取得できます。  次の例では、<xref:System.Windows.Forms.SystemInformation> クラスを使用して <xref:System.Windows.Forms.SystemInformation.UserName%2A> および <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A> を取得する方法を示しています。  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to " _  
+ Domain)  
```  
  
 <xref:System.Windows.Forms.SystemInformation> クラスのすべてのメンバーは、読み取り専用です。ユーザーの設定を変更することはできません。  クラスには、コンピューターに接続されているモニターの数を返すもの \(<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>\) から、Windows エクスプローラーのアイコンの間隔を返すもの \(<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> および <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>\) まで、100 を超えるメンバーがあります。  
  
 <xref:System.Windows.Forms.SystemInformation> クラスにおける有用なメンバーには、<xref:System.Windows.Forms.SystemInformation.ComputerName%2A>、<xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>、<xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>、および <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A> があります。  
  
## 参照  
 <xref:System.Windows.Forms.SystemInformation>   
 [Windows フォームでの電源管理](../../../../docs/framework/winforms/advanced/power-management-in-windows-forms.md)