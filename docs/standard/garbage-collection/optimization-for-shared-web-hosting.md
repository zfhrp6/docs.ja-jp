---
title: "共有 Web ホストの最適化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f423d867d4fada075800650627c94f9d09e9e7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="optimization-for-shared-web-hosting"></a>共有 Web ホストの最適化
複数の小規模 Web サイトをホストすることにより共有されているサーバーの管理者がいる場合は、パフォーマンスを最適化し、次を追加することによってサイト容量を増やす`gcTrimCommitOnLowMemory`設定、 `runtime` .net Aspnet.config ファイル内のノードディレクトリ:  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  この設定は推奨のみ共有 Web をホスティングのシナリオです。  
  
 ガベージ コレクターは、将来の割り当て用のメモリを保持しているためにより厳密に必要なものをコミットされた領域にできます。 時刻を格納するには、この領域を減らすことができますが、システム メモリの負荷が高い場合。 このコミットされた領域を減らすことにより、パフォーマンスが向上しより多くのサイトをホストする能力を展開します。  
  
 ときに、`gcTrimCommitOnLowMemory`設定が有効になっていると、ガベージ コレクターは、システム メモリの負荷を評価し、負荷が 90% に達すると、トリミング モードに入ります。 負荷が 85% を未満になるまで、トリミング モードが維持されます。  
  
 条件は次の許可、ガベージ コレクター場合ことができますを`gcTrimCommitOnLowMemory`設定されず、現在のアプリケーションのヘルプ、それを無視します。  
  
## <a name="example"></a>例  
 次の XML フラグメントが有効にする方法を示しています、`gcTrimCommitOnLowMemory`設定します。 省略記号ボタンを示すようになります。 その他の設定、`runtime`ノード。  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [ガベージ コレクション](../../../docs/standard/garbage-collection/index.md)
