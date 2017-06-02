---
title: "Windows フォームでのより安全な印刷 | Microsoft Docs"
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
  - "印刷 [Windows フォーム], セキュリティ"
  - "PrintingPermission クラス, Windows フォームのセキュリティ"
  - "セキュリティ [Windows フォーム], 印刷"
  - "Windows フォーム, 印刷"
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Windows フォームでのより安全な印刷
多くの Windows フォーム アプリケーションは、印刷機能を備えています。  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、<xref:System.Drawing.Printing.PrintingPermission> クラスを使用して印刷機能へのアクセスを制御し、これに関連付けられている <xref:System.Drawing.Printing.PrintingPermissionLevel> 列挙値を使用してアクセスのレベルを示します。  \[イントラネット\] ゾーンと \[インターネット\] ゾーンでは、既定で印刷が有効になっています。ただし、アクセスのレベルはどちらのゾーンも制限されています。  アプリケーションが印刷を実行できるか、ユーザーとの対話が必要か、または印刷を実行できないかは、アプリケーションに与えられているアクセス許可の値によって異なります。  既定では、\[イントラネット\] ゾーンでは <xref:System.Drawing.Printing.PrintingPermissionLevel> アクセスが許可され、\[インターネット\] ゾーンでは <xref:System.Drawing.Printing.PrintingPermissionLevel> アクセスが許可されます。  
  
 各印刷アクセス許可レベルで使用できる機能を次の表に示します。  
  
|PrintingPermissionLevel|Description|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel>|インストールされているすべてのプリンターに対して完全なアクセス権限が与えられます。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel>|既定のプリンターへのプログラムによる印刷、および制限付きの印刷ダイアログ ボックスを使用した安全な印刷を有効にします。  <xref:System.Drawing.Printing.PrintingPermissionLevel> は <xref:System.Drawing.Printing.PrintingPermissionLevel> のサブセットです。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel>|より制限されたダイアログ ボックスからの印刷だけが許可されます。  <xref:System.Drawing.Printing.PrintingPermissionLevel> は <xref:System.Drawing.Printing.PrintingPermissionLevel> のサブセットです。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel>|プリンターへのアクセスを防止します。  <xref:System.Drawing.Printing.PrintingPermissionLevel> は <xref:System.Drawing.Printing.PrintingPermissionLevel> のサブセットです。|  
  
## 参照  
 [Windows フォームにおけるファイルおよびデータへのより安全なアクセス](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)   
 [Windows フォームのセキュリティに関するその他の考慮事項](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)   
 [Windows フォームのセキュリティの概要](../../../docs/framework/winforms/security-in-windows-forms-overview.md)   
 [Windows フォームのセキュリティ](../../../docs/framework/winforms/windows-forms-security.md)