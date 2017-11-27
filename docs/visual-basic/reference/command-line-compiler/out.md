---
title: /out (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d98a9f3cadc42021c302915cfc5b058b41e11ec6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="out-visual-basic"></a>/out (Visual Basic)
出力ファイルの名前を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/out:filename  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`filename`|必須です。 コンパイラの出力ファイルの名前を作成します。 ファイル名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。|  
  
## <a name="remarks"></a>コメント  
 完全な名前とを作成するファイルの拡張子を指定します。 .Exe ファイルが、ソース コードを含むファイルから名前を取得しない場合、`Sub Main`プロシージャと .dll ファイルは、最初のソース コード ファイルの名前がします。  
  
 .Exe または .dll 拡張子を持たないファイル名を指定する場合、コンパイラ自動的に追加、拡張機能に指定された値によって、`/target`コンパイラ オプション。  
  
|Visual Studio 統合開発環境で/out を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.**[アプリケーション]** タブをクリックします。<br />3.値を変更、**アセンブリ名**ボックス。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`出力ファイルが作成および`T2.exe`です。  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
