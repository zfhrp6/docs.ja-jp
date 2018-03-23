---
title: -参照 (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba879dd7079b35bea50c4a6c1d67da7aa57110f6
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-reference-visual-basic"></a>-参照 (Visual Basic)
コンパイラで指定されたアセンブリ内の型情報をプロジェクトのコンパイル中にできるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`fileList`|必須。 アセンブリ ファイル名のコンマ区切りリスト。 ファイル名に空白が含まれている場合は、名前を二重引用符で囲みます。|  
  
## <a name="remarks"></a>コメント  
 インポートするファイルは、アセンブリ メタデータを含める必要があります。 パブリック型だけでは、アセンブリの外側に表示されます。 [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)オプションは、モジュールからメタデータをインポートします。  
  
 アセンブリ (アセンブリ A) を参照する場合は、別のアセンブリ (アセンブリ B) を参照する、必要な参照アセンブリ B 場合。  
  
-   アセンブリ A の型がアセンブリ B の型から継承されているか、アセンブリ B のインターフェイスを実装する。  
  
-   アセンブリ B の戻り値の型またはパラメーターの型を使用するフィールド、プロパティ、イベント、またはメソッドが呼び出される。  
  
 使用して[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)を 1 つ以上のアセンブリ参照があるディレクトリを指定します。  
  
 アセンブリ モジュールではなく) 内の型を認識するようにコンパイラで型の解決を強制する必要があります。 この操作方法の 1 つの例では、型のインスタンスを定義します。 その他の方法は、コンパイラがアセンブリ内の型名を解決するには利用できます。 たとえば、アセンブリ内の型から継承する場合、型名し既知となるコンパイラにします。  
  
 参照がよく使用される、Vbc.rsp 応答ファイル[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリは既定で使用します。 使用して`-noconfig`コンパイラが Vbc.rsp を使用したくない場合。  
  
 `-reference` の省略形は `/r` です。  
  
## <a name="example"></a>例  
 次のコマンドは、ソース ファイルをコンパイル`Input.vb`からアセンブリを参照および`Metad1.dll`と`Metad2.dll`を生成する`Out.exe`です。  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
