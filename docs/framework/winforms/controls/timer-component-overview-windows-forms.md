---
title: "Timer コンポーネントの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a467cb266f284e2bfdedbb5061f26231736af2b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="timer-component-overview-windows-forms"></a>Timer コンポーネントの概要 (Windows フォーム)
Windows フォーム <xref:System.Windows.Forms.Timer> は、一定の間隔でイベントを発生させるコンポーネントです。 このコンポーネントは、Windows フォームの環境用に設計されています。 サーバー環境に適したタイマーが必要な場合は、「[サーバー ベースのタイマーの概要](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)」を参照してください。  
  
## <a name="key-properties-methods-and-events"></a>キー プロパティ、メソッド、およびイベント  
 間隔の長さがによって定義された、<xref:System.Windows.Forms.Timer.Interval%2A>プロパティ、値を持つ単位はミリ秒です。 コンポーネントが有効にすると、<xref:System.Windows.Forms.Timer.Tick>イベントが発生したすべての間隔。 これは、実行するコードを追加することです。 詳細については、次を参照してください。[する方法: Windows フォームの Timer コンポーネントの設定間隔でプロシージャの実行](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md)です。 主要なメソッド、<xref:System.Windows.Forms.Timer>コンポーネントは<xref:System.Windows.Forms.Timer.Start%2A>と<xref:System.Windows.Forms.Timer.Stop%2A>タイマーをオンまたはオフにします。 タイマーをオフにすると、ときにリセットされます。一時停止する方法はありません、<xref:System.Windows.Forms.Timer>コンポーネントです。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Timer>  
 [Timer コンポーネント](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Windows フォームの Timer コンポーネントの Interval プロパティの制限](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
