---
title: コールバック メソッドとしてのデリゲートのマーシャ リング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff875f2807a14493ab81a9e354b5c4dcdf3d5feb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389384"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a>コールバック メソッドとしてのデリゲートのマーシャ リング
このサンプルでは、関数ポインターを要求するアンマネージ関数にデリゲートを渡す方法を示します。 デリゲートは、メソッドへの参照を保持できるクラスであり、タイプ セーフな関数ポインターまたはコールバック関数と同等のものです。  
  
> [!NOTE]
>  呼び出しの中でデリゲートを使うと、共通言語ランタイムがデリゲートをその呼び出しの期間中ガベージ コレクションから保護します。 ただし、アンマネージ関数が呼び出し完了後に使うためにデリゲートを保存する場合は、アンマネージ関数がデリゲートを終了するまで手動でガベージ コレクションを防ぐ必要があります。 詳細については、「[HandleRef Sample](https://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959(v=vs.100))」(HandleRef のサンプル) および「[GCHandle Sample](https://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f(v=vs.100))」(GCHandle のサンプル) をご覧ください。  
  
 Callback のサンプルで使用するアンマネージ関数とその元の関数宣言を次に示します。  
  
-   PinvokeLib.dll からエクスポートされる **TestCallBack**。  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   PinvokeLib.dll からエクスポートされる **TestCallBack2**。  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) はカスタム アンマネージ ライブラリであり、上で示した関数の実装を含んでいます。  
  
 このサンプルでは、`LibWrap` クラスには、`TestCallBack` メソッドと `TestCallBack2` メソッドのマネージ プロトタイプが含まれます。 どちらのメソッドも、コールバック関数にパラメーターとしてデリゲートを渡します。 デリゲートのシグネチャは、それが参照しているメソッドのシグネチャと一致する必要があります。 たとえば、`FPtr` および `FPtr2` デリゲートのシグネチャは、`DoSomething` および `DoSomething2` メソッドと同じです。  
  
## <a name="declaring-prototypes"></a>プロトタイプの宣言  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a>関数の呼び出し  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a>参照  
 [各種のマーシャリングのサンプル](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))  
 [プラットフォーム呼び出しのデータ型](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [マネージ コードでのプロトタイプの作成](creating-prototypes-in-managed-code.md)
