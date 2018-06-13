---
title: 競合 ETW イベント
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3487b67ea49cecfd0da2b5b3f993ea54d562145d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397521"
---
# <a name="contention-etw-events"></a>競合 ETW イベント
競合イベントは、ランタイムによって使用される <xref:System.Threading.Monitor?displayProperty=nameWithType> ロックまたはネイティブ ロックの競合が発生するたびに発生します。 競合は、あるスレッドが、別のスレッドが保持しているロックを待機しているときに発生します。  
  
 競合イベントが発生するキーワードとイベントのレベルを次の表に示します  (詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。  
  
|イベントを発生させるキーワード|レベル|  
|-----------------------------------|-----------|  
|`ContentionKeyword` (0x4000)|情報提供 (4)|  
  
 次の表にイベント情報を示します。  
  
|event|イベント ID|いつ発生するか|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|81|競合が開始されたとき。 このイベントには、スレッドがロックの取得を待機する前のスピン時間は含まれません。このイベントが発生するのは、スレッドがロックの取得を待機するときだけです。|  
|`ContentionStop`|81|競合が終了したとき。|  
  
 次の表にイベント データを示します。  
  
|フィールド名|データ型|説明|  
|----------------|---------------|-----------------|  
|フラグ|win:UInt8|マネージの場合は 0、ネイティブの場合は 1 です。|  
|ClrInstanceID|win:UInt16|CLR のインスタンスの一意の ID。|  
  
## <a name="see-also"></a>関連項目  
 [CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)
