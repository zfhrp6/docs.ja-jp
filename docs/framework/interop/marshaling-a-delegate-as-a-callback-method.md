---
title: "コールバック メソッドとしてのデリゲートのマーシャ リング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "データ マーシャリング, Callback サンプル"
  - "マーシャリング, Callback サンプル"
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# コールバック メソッドとしてのデリゲートのマーシャ リング
このサンプルでは、関数ポインターを要求するアンマネージ関数にデリゲートを渡す方法を示します。  デリゲートは、メソッドへの参照を保持できるクラスのことであり、タイプ セーフ関数ポインターまたはコールバック関数と等価です。  
  
> [!NOTE]
>  呼び出しの中でデリゲートを使用する場合、共通言語ランタイムは、呼び出しの間にデリゲートがガベージ コレクトされないように保護します。  ただし、呼び出しが完了した後で使用するためにアンマネージ関数がデリゲートを格納する場合には、アンマネージ関数がデリゲートを終了するまでの間、手動でガベージ コレクションを防ぐ必要があります。  詳細については、「[HandleRef のサンプル](http://msdn.microsoft.com/ja-jp/ab23b04e-1d53-4ec7-b27a-e892d9298959)」および「[GCHandle のサンプル](http://msdn.microsoft.com/ja-jp/6acce798-0385-4ded-a790-77da842c113f)」を参照してください。  
  
 Callback のサンプルで使用するアンマネージ関数とその関数宣言を次に示します。  
  
-   PinvokeLib.dll からエクスポートされる **TestCallBack**  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   PinvokeLib.dll からエクスポートされる **TestCallBack2**  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 [PinvokeLib.dll](http://msdn.microsoft.com/ja-jp/5d1438d7-9946-489d-8ede-6c694a08f614) はカスタム アンマネージ ライブラリであり、上記の関数に関する実装を含みます。  
  
 このサンプルでは、`LibWrap` クラスには `TestCallBack` メソッドと `TestCallBack2` メソッドに関するマネージ プロトタイプが含まれます。  どちらのメソッドも、コールバック関数にパラメーターとしてデリゲートを渡します。  デリゲートのシグネチャは、その参照先メソッドのシグネチャと一致する必要があります。  たとえば、デリゲートの `FPtr` と `FPtr2` は、`DoSomething` メソッドおよび `DoSomething2` メソッドと同じシグネチャを持ちます。  
  
## プロトタイプの宣言  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## 関数の呼び出し  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## 参照  
 [Miscellaneous Marshaling Samples](http://msdn.microsoft.com/ja-jp/a915c948-54e9-4d0f-a525-95a77fd8ed70)   
 [Platform Invoke Data Types](http://msdn.microsoft.com/ja-jp/16014d9f-d6bd-481e-83f0-df11377c550f)   
 [マネージ コードでのプロトタイプの作成](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)