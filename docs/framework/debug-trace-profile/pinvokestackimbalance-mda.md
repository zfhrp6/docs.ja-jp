---
title: pInvokeStackImbalance MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9938db3f4a3d054fde52139c166fb6a2e2a402df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="pinvokestackimbalance-mda"></a>pInvokeStackImbalance MDA
<xref:System.Runtime.InteropServices.DllImportAttribute> の属性で指定される呼び出し規約、およびマネージ シグネチャ内のパラメーターの宣言が指定されている場合に、プラットフォーム呼び出しが、予想されるスタックの深さに一致しないことを CLR が検出したときに、`pInvokeStackImbalance` マネージ デバッグ アシスタント (MDA) がアクティブ化されます。  
  
> [!NOTE]
>  `pInvokeStackImbalance` MDA は 32 ビット x86 プラットフォームに対してのみ実装されています。  
  
> [!NOTE]
>  .NET Framework version 3.5 で、 `pInvokeStackImbalance` MDA は既定で無効になります。 .NET Framework version 3.5 と Visual Studio 2005 を使用すると、`pInvokeStackImbalance` MDA が **[例外]** ダイアログ ボックス (**[デバッグ]** メニューの **[例外]** をクリックすると表示される) の **[マネージ デバッグ アシスタント]** の一覧に表示されます。 ただし、`pInvokeStackImbalance` の **[スローされるとき]** のチェック ボックスをオンまたはオフにしても、MDA は有効または無効になりません。MDA がアクティブ化されたときに Visual Studio が例外をスローするかどうかのみを制御します。  
  
## <a name="symptoms"></a>現象  
 プラットフォーム呼び出しの実行時または実行後に、アプリケーションでアクセス違反またはメモリ破損が発生します。  
  
## <a name="cause"></a>原因  
 プラットフォーム呼び出しのマネージ シグネチャが、呼び出されているメソッドのアンマネージ シグネチャと一致しない可能性があります。  この不一致は、正しい数のパラメーターを宣言しないか、適切なサイズのパラメーターを指定しないマネージ シグネチャで発生する可能性があります。  また、<xref:System.Runtime.InteropServices.DllImportAttribute> 属性によって指定されている可能性がある呼び出し規約が、アンマネージ呼び出し規約と一致しない場合にも、MDA がアクティブ化される可能性があります。  
  
## <a name="resolution"></a>解像度  
 マネージ プラットフォーム呼び出しシグネチャ、および呼び出し規則を確認して、ネイティブ ターゲットのシグネチャと呼び出し規約に一致することを確認します。  マネージ側とアンマネージ側の両方で、呼び出し規約を明示的に指定してください。 また、あまり可能性はありませんが、アンマネージ コンパイラのバグなど、何らかの理由によりアンマネージ関数でスタックの不均衡が発生している場合もあります。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 すべてのプラットフォーム呼び出しが、CLR の最適化されていないパスを取得するよう強制します。  
  
## <a name="output"></a>出力  
 MDA メッセージが、スタックの不均衡の原因であるプラットフォーム呼び出しメソッド呼び出しの名前を示します。  メソッド `SampleMethod` のプラットフォーム呼び出しのサンプル メッセージは、次のとおりです。  
  
```  
A call to PInvoke function 'SampleMethod' has unbalanced the stack.   
This is likely because the managed PInvoke signature does not match   
the unmanaged target signature. Check that the calling convention and   
parameters of the PInvoke signature match the target unmanaged signature.  
```  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeStackImbalance />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [マネージ デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)
