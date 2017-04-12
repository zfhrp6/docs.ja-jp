---
title: "/nostdlib (Visual Basic) |Microsoft ドキュメント"
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
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 3bacd7d51d12ec6c48dc11ff4b83d842a9e78a30
ms.lasthandoff: 03/13/2017

---
# <a name="nostdlib-visual-basic"></a>/nostdlib (Visual Basic)
コンパイラが自動的に標準のライブラリを参照します。  
  
## <a name="syntax"></a>構文  
  
```  
/nostdlib  
```  
  
## <a name="remarks"></a>コメント  
 `/nostdlib`  オプションは、System.dll アセンブリへの自動参照を削除され、コンパイラが、Vbc.rsp ファイルの読み取りができなくなります。 Vbc.rsp ファイル-Vbc.exe ファイルと同じディレクトリにある、一般的に使用される参照[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アセンブリとインポート、`System`と`Microsoft.VisualBasic`名前空間。  
  
> [!NOTE]
>  Mscorlib.dll および Microsoft.VisualBasic.dll のアセンブリは常に参照します。  
  
> [!NOTE]
>  `/nostdlib`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`標準ライブラリを参照しなくてもします。 設定する必要があります、`_MYTYPE`条件付きコンパイル定数文字列を削除するには、「空」を`My`オブジェクトです。  
  
```  
vbc /nostdlib /define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [My で利用可能なオブジェクトのカスタマイズ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
