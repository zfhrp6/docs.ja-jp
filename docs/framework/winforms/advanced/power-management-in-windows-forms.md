---
title: Windows フォームでの電源管理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 845cc9c910d63dfc7460bba0d5368b5b1e63efcd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523492"
---
# <a name="power-management-in-windows-forms"></a>Windows フォームでの電源管理
Windows フォーム アプリケーションを利用、電源管理機能の Windows オペレーティング システムにできます。 アプリケーションでは、コンピューターの電源の状態を監視でき、状態の変更が発生したときにアクションを実行することができます。 たとえば、アプリがポータブル コンピューターで実行されている場合可能性がある、コンピューターのバッテリ充電量が一定のレベルを下回ったときに、アプリケーションで特定の機能を無効にします。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]提供、<xref:Microsoft.Win32.SystemEvents.PowerModeChanged>電源の状態、または AC 電源の状態またはバッテリの状態が変更されたときにユーザーを中断またはオペレーティング システムを再開する場合などに変更があるときに発生するイベントです。 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>のプロパティ、<xref:System.Windows.Forms.SystemInformation>できるクラスは次のコード例に示すように現在の状態では、クエリを使用します。  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 以外にも、<xref:System.Windows.Forms.BatteryChargeStatus>列挙型、<xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>プロパティには、バッテリ容量を決定するための列挙型も含まれています (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) およびバッテリの充電の割合 (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>、 <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>)。  
  
 使用することができます、<xref:System.Windows.Forms.Application.SetSuspendState%2A>のメソッド、<xref:System.Windows.Forms.Application>コンピューターを休止状態または中断モードにします。 場合、`force`に設定されている引数`false`、オペレーティング システムが中断するアクセス許可を要求するすべてのアプリケーションにイベントをブロードキャストします。 場合、`disableWakeEvent`に設定されている引数`true`、オペレーティング システムのスリープ解除のすべてのイベントを無効にします。  
  
 次のコード例では、コンピューターを休止状態にする方法を示します。  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>  
 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>  
 <xref:System.Windows.Forms.Application.SetSuspendState%2A>  
 <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
