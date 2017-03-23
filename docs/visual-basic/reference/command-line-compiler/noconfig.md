---
title: "/noconfig |Microsoft ドキュメント"
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
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: 15
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
ms.openlocfilehash: 304d0e7fc787adb1d7776a2c047090ffc230fcc1
ms.lasthandoff: 03/13/2017

---
# <a name="noconfig"></a>/noconfig
コンパイラが含まれていないことに自動的に一般的に使用される指定[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アセンブリまたはインポート、`System`と`Microsoft.VisualBasic`名前空間。  
  
## <a name="syntax"></a>構文  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a>コメント  
 `/noconfig`オプション Vbc.exe ファイルと同じディレクトリにあると、Vbc.rsp ファイルでコンパイルしていないコンパイラに指示します。 Vbc.rsp ファイルを参照して、一般的に使用される[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アセンブリとインポート、`System`と`Microsoft.VisualBasic`名前空間。 しない限り、System.dll アセンブリが、コンパイラによって暗黙的に参照、`/nostdlib`オプションを指定します。 `/nostdlib`オプションと、Vbc.rsp でコンパイルや System.dll アセンブリを自動的に参照を行わないコンパイラに指示します。  
  
> [!NOTE]
>  Mscorlib.dll および Microsoft.VisualBasic.dll のアセンブリは常に参照します。  
  
 すべて Vbc.exe のコンパイル時に含める必要がある追加のコンパイラ オプションを指定すると、Vbc.rsp ファイルを変更することができます (を指定する場合を除いて、`/noconfig`オプション)。 詳しくは、「[@ (応答ファイルの指定)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)」をご覧ください。  
  
 コンパイラに渡されるオプションの処理、`vbc`コマンドの最後です。 そのため、コマンドラインに指定したオプションは、Vbc.rsp ファイル内の同じオプションの設定を上書きします。  
  
> [!NOTE]
>  `/noconfig`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。  
  
## <a name="see-also"></a>関連項目  
 [/nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)   
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)   
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
