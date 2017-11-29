---
title: "制限事項の Windows フォームの Timer コンポーネント &#39; s 間隔プロパティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72af16b7dcb7709dd132a3748a454eda57acc168
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a>制限事項の Windows フォームの Timer コンポーネント &#39; s 間隔プロパティ
Windows フォーム<xref:System.Windows.Forms.Timer>コンポーネントには、<xref:System.Windows.Forms.Timer.Interval%2A>と次の 1 つのタイマー イベント間で渡されるミリ秒数を指定するプロパティです。 タイマーは引き続き受信コンポーネントが無効にしない限り、<xref:System.Windows.Forms.Timer.Tick>ほぼ一定時間の間隔でイベント。  
  
 このコンポーネントは、Windows フォームの環境用に設計されています。 サーバー環境に適したタイマーが必要な場合は、「[サーバー ベースのタイマーの概要](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)」を参照してください。  
  
## <a name="the-interval-property"></a>間隔のプロパティ  
 <xref:System.Windows.Forms.Timer.Interval%2A>プロパティがプログラミングしているときに考慮すべきいくつかの制限、<xref:System.Windows.Forms.Timer>コンポーネント。  
  
-   アプリケーションまたは別のアプリケーションで、システムで重い負荷が早い場合 — 長いループや複雑な計算、またはドライブ、ネットワーク、またはポートへのアクセスなど、アプリケーションとしてのタイマー イベントを頻繁に利用できない、<xref:System.Windows.Forms.Timer.Interval%2A>プロパティを指定します。  
  
-   間隔は、正確に時間の経過時間は保証されません。 精度を保証するには、タイマー必要があります、必要に応じて、システム クロックのチェックではなく保持の累積時間を内部的にしようとしています。  
  
-   有効桁数、<xref:System.Windows.Forms.Timer.Interval%2A>プロパティは、(ミリ秒単位)。 一部のコンピューターでは、ミリ秒単位より高い解像度が高解像度カウンターを提供します。 このようなカウンターの可用性は、コンピューターのプロセッサ ハードウェアに依存します。 詳細については、172338、「どのように使用 QueryPerformanceCounter に時間コードへ、」http://support.microsoft.com にで、Microsoft サポート技術情報の記事を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Timer>  
 [Timer コンポーネント](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Timer コンポーネントの概要](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
