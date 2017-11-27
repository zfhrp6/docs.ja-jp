---
title: "コールバック メソッドとしてのデリゲートのマーシャ リング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c8c4eca35c406b38da603dc10358920ee887b137
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a>コールバック メソッドとしてのデリゲートのマーシャ リング
このサンプルでは、関数ポインターを要求するアンマネージ関数にデリゲートを渡す方法を示します。 デリゲートは、メソッドへの参照を保持できるクラスであり、タイプ セーフな関数ポインターまたはコールバック関数と同等のものです。  
  
> [!NOTE]
>  呼び出しの中でデリゲートを使うと、共通言語ランタイムがデリゲートをその呼び出しの期間中ガベージ コレクションから保護します。 ただし、アンマネージ関数が呼び出し完了後に使うためにデリゲートを保存する場合は、アンマネージ関数がデリゲートを終了するまで手動でガベージ コレクションを防ぐ必要があります。 詳細については、「[HandleRef Sample](http://msdn.microsoft.com/en-us/ab23b04e-1d53-4ec7-b27a-e892d9298959)」(HandleRef のサンプル) および「[GCHandle Sample](http://msdn.microsoft.com/en-us/6acce798-0385-4ded-a790-77da842c113f)」(GCHandle のサンプル) をご覧ください。  
  
 Callback のサンプルで使用するアンマネージ関数とその元の関数宣言を次に示します。  
  
-   PinvokeLib.dll からエクスポートされる **TestCallBack**。  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   PinvokeLib.dll からエクスポートされる **TestCallBack2**。  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 [PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) はカスタム アンマネージ ライブラリであり、上で示した関数の実装を含んでいます。  
  
 このサンプルでは、`LibWrap` クラスには、`TestCallBack` メソッドと `TestCallBack2` メソッドのマネージ プロトタイプが含まれます。 どちらのメソッドも、コールバック関数にパラメーターとしてデリゲートを渡します。 デリゲートのシグネチャは、それが参照しているメソッドのシグネチャと一致する必要があります。 たとえば、`FPtr` および `FPtr2` デリゲートのシグネチャは、`DoSomething` および `DoSomething2` メソッドと同じです。  
  
## <a name="declaring-prototypes"></a>プロトタイプの宣言  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a>関数の呼び出し  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a>関連項目  
 [各種のマーシャリングのサンプル](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)  
 [プラットフォーム呼び出しのデータ型](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [マネージ コードでのプロトタイプの作成](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
