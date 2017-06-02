---
title: "Windows フォームで ActiveX コントロールをホストする場合の考慮事項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ActiveX コントロール [Windows フォーム], 追加"
  - "ActiveX コントロール [Windows フォーム], ホスト"
  - "Windows フォーム コントロール, ActiveX コントロール"
  - "Windows フォーム, ActiveX コントロール"
  - "Windows フォーム, ホスト (ActiveX コントロールを)"
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Windows フォームで ActiveX コントロールをホストする場合の考慮事項
Windows フォームは、Windows フォーム コントロールをホストするために最適化されていますが、代わりに ActiveX コントロールも使用できます。  アプリケーションで ActiveX コントロールを使用する場合には、以下の点を考慮してください。  
  
-   **セキュリティ** 共通言語ランタイムは、コード アクセスのセキュリティについて強化されています。  Windows フォームを使用するアプリケーションは、問題のない完全に信頼できる環境で実行するか、またはほとんどの機能にアクセスできる、やや信頼性の低い環境で実行できます。  Windows フォーム コントロールは、ブラウザーで簡単にホストできます。  ただし、Windows フォーム上の ActiveX コントロールでは、これらのセキュリティの拡張機能を利用できません。  ActiveX コントロールの実行には、<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=fullName> プロパティで設定されるアンマネージ コード アクセス許可が必要です。  セキュリティおよびアンマネージ コード アクセス許可の詳細については、「[SecurityPermissionAttribute クラス](frlrfSystemSecurityPermissionsSecurityPermissionAttributeClassTopic)」を参照してください。  
  
-   **TCO \(Total Cost of Ownership\)** Windows フォームに追加された ActiveX コントロールは、その全体が Windows フォームと共に配置されるため、作成されるファイルのサイズがかなり大きくなる場合があります。  また、Windows フォーム上で ActiveX コントロールを使用するには、レジストリへの書き込みが必要です。  そのため、レジストリへの書き込みを必要としない Windows フォーム コントロールに比べて、ユーザーがコンピューターに干渉する度合いが大きくなります。  
  
    > [!NOTE]
    >  ActiveX コントロールを使用するには、COM 相互運用ラッパーが必要です。  詳細については、「[Visual Basic および Visual C\# における COM 相互運用性](../Topic/COM%20Interoperability%20in%20.NET%20Framework%20Applications%20\(Visual%20Basic\).md)」を参照してください。  
  
    > [!NOTE]
    >  ActiveX コントロールの中に、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] で定義されている名前と同じ名前のメンバーがある場合、<xref:System.Windows.Forms.AxHost> の派生クラスの作成時に、ActiveX コントロール インポーターによって、これらのメンバーにプレフィックス **Ctl** が付けられます。  たとえば、ActiveX コントロールに **Layout** という名前のメンバーが含まれる場合、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] に **Layout** イベントが定義されているため、AxHost 派生クラスでは **CtlLayout** という名前に変更されます。  
  
## 参照  
 [方法 : Windows フォームに ActiveX コントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)   
 [コード アクセス セキュリティ](../../../../docs/framework/misc/code-access-security.md)   
 [Controls and Programmable Objects Compared in Various Languages and Libraries](http://msdn.microsoft.com/ja-jp/021f2a1b-8247-4348-a5ad-e1d9ab23004b)   
 [Windows フォームへのコントロールの追加](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)   
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)