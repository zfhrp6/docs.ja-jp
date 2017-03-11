---
title: "&lt;proceduresignature1&gt; is not CLS-compliant because it overloads &lt;proceduresignature2&gt; which differs from it only by array of array parameter types or by the rank of the array parameter types | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc40035"
  - "bc40035"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40035"
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# &lt;proceduresignature1&gt; is not CLS-compliant because it overloads &lt;proceduresignature2&gt; which differs from it only by array of array parameter types or by the rank of the array parameter types
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

別のプロシージャまたはプロパティをオーバーライドしているプロシージャまたはプロパティが `<CLSCompliant(True)>` でマーク付けされていますが、両者のパラメーター リストには、ジャグ配列の入れ子レベルまたは配列のランクの違いしかありません。  
  
 次の 3 つの宣言のうち、2 番目と 3 番目の宣言ではエラーが発生します。  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 2 番目の宣言では、最初の 1 次元のパラメーター `arrayParam` が配列の配列に変更されています。  3 番目の宣言では、`arrayParam` が 2 次元配列 \(ランク 2\) に変更されています。  Visual Basic ではこれらの変更のいずれか 1 つだけの違いでオーバーロードすることが可能ですが、このようなオーバーロードは [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) に準拠しません。  
  
 <xref:System.CLSCompliantAttribute> をプログラミング要素に適用するときは、属性の `isCompliant` パラメーターを `True` または `False` に設定して準拠または非準拠を示します。  このパラメーターの既定値はありません。値を指定する必要があります。  
  
 <xref:System.CLSCompliantAttribute> を要素に適用しなかった場合は、非準拠と見なされます。  
  
 既定では、このメッセージは警告です。  警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic) を参照してください。  
  
 **Error ID:** BC40035  
  
### このエラーを解決するには  
  
-   CLS に準拠させる必要がある場合は、ここに示した変更点だけでなく、相互により多くの違いを持つようにオーバーロードを定義します。  
  
-   ここで示した変更点だけでオーバーロードを定義する必要がある場合は、<xref:System.CLSCompliantAttribute> を定義から削除するか、`<CLSCompliant(False)>` でマーク付けします。  
  
## 参照  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)