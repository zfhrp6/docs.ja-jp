---
title: Windows フォームでのより安全な印刷
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 976079f39e13186014b77e85c092c37be11238b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538940"
---
# <a name="more-secure-printing-in-windows-forms"></a>Windows フォームでのより安全な印刷
Windows フォーム アプリケーションには、印刷機能を備えて頻繁に含まれます。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]を使用して、<xref:System.Drawing.Printing.PrintingPermission>クラスからの印刷機能へのアクセス制御および関連付けられた<xref:System.Drawing.Printing.PrintingPermissionLevel>アクセスのレベルを示す列挙値。 既定では、既定では、ローカルのイントラネットとインターネット ゾーンで印刷が有効にします。ただし、アクセスのレベルは、両方の領域で制限されます。 ユーザーとのやり取りが必要だかどうかを印刷できるアプリケーション、または印刷は、アプリケーションに付与されるアクセス許可の値に依存できません。 ローカル イントラネット ゾーンでは既定では、<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>とイントラネット ゾーンのアクセスを受け取る<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>アクセスします。  
  
 次の表は、各印刷アクセス許可レベルで使用できる機能を示します。  
  
|PrintingPermissionLevel|説明|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|インストールされているすべてのプリンターへのフル アクセスを提供します。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|既定のプリンターにプログラムによる印刷および制限の厳しい印刷 ダイアログ ボックスを経由した安全な印刷を有効にします。 <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> は <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting> のサブセットです。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|制限されたダイアログ ボックスからのみ印刷機能を提供します。 <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> は <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> のサブセットです。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|プリンターにアクセスできなくなります。 <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> は <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> のサブセットです。|  
  
## <a name="see-also"></a>関連項目  
 [Windows フォームにおけるファイルおよびデータへのより安全なアクセス](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [Windows フォームのセキュリティに関するその他の考慮事項](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [Windows フォームのセキュリティの概要](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Windows フォームのセキュリティ](../../../docs/framework/winforms/windows-forms-security.md)
