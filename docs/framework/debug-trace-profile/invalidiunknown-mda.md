---
title: invalidIUnknown MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 970d4dddd473fc671da510cb76b35eca94c55af9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="invalidiunknown-mda"></a>invalidIUnknown MDA
`invalidIUnknown` マネージ デバッグ アシスタント (MDA: Managed Debugging Assistant) は、無効な `IUnknown` ポインターがネイティブ コードからマネージ コードに渡されるとアクティブ化されます。 `IUnknown` インターフェイスが照会されたときに、`IUnknown` は、成功したことを返すことができませんでした。  
  
## <a name="symptoms"></a>症状  
 引数のマーシャリング中に COM インターフェイス ポインターをマーシャリングすると、予期しないエラーが発生します。  
  
## <a name="cause"></a>原因  
 CLR に渡された COM インターフェイスで、`QueryInterface` の実装が正しくありません。  
  
## <a name="resolution"></a>解決策  
 `QueryInterface` の実装を修正します。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 この MDA は CLR に影響しません。  
  
## <a name="output"></a>出力  
 エラーの説明です。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [マネージ デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)

