---
title: "/reference (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 12344dba82131d6be2c32127de287a6e9e3efa39
ms.lasthandoff: 03/13/2017

---
# <a name="reference-visual-basic"></a>/reference (Visual Basic)
コンパイラで指定したアセンブリ内の型情報をプロジェクトのコンパイル中にできるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`fileList`|必須です。 アセンブリ ファイル名のコンマ区切りリスト。 ファイル名にスペースが含まれている場合は、名前を引用符で囲みます。|  
  
## <a name="remarks"></a>コメント  
 インポートするファイルは、アセンブリ メタデータを含める必要があります。 パブリック型だけでは、アセンブリの外側に表示されます。 [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)オプションは、モジュールからメタデータをインポートします。  
  
 アセンブリ (アセンブリ A) を参照する場合は、別のアセンブリ (アセンブリ B) を参照する場合に、アセンブリ B を参照する必要は。  
  
-   アセンブリ A から型の型から継承またはアセンブリ B のインターフェイスを実装します。  
  
-   フィールド、プロパティ、イベント、またはアセンブリ B の戻り値の型またはパラメーターの型を持つメソッドが呼び出されます。  
  
 使用[/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)を&1; つ以上のアセンブリ参照があるディレクトリを指定します。  
  
 コンパイラがアセンブリ (モジュールではなく) の型を認識するには、型の解決を強制する必要があります。 この操作方法の&1; つの例では、型のインスタンスを定義します。 その他の方法は、コンパイラがアセンブリ内の型名を解決するには使用できます。 たとえば、アセンブリ内の型から継承する場合、型名し、既知となるコンパイラにします。  
  
 参照は通常、使用、Vbc.rsp 応答ファイル[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アセンブリが既定で使用します。 使用して`/noconfig`Vbc.rsp を使うようコンパイラにしたくない場合。  
  
 短い形式の`/reference`は`/r`です。  
  
## <a name="example"></a>例  
 次のコードのコンパイルのソース ファイルは`nput.vb`M からアセンブリを参照および`etad1.dll`と M`etad2.dll` O を生成する`ut.exe`です。  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [パブリック](../../../visual-basic/language-reference/modifiers/public.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
