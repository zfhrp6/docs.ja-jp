---
title: /libpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2be2c460fddf2e8ea4fe1239ec073f208c072d34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="libpath"></a>/libpath
参照先アセンブリの場所を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`dirList`|必須です。 コンパイラが参照先アセンブリを探す場合にディレクトリのセミコロン区切りのリストに載っていないいずれかの現在の作業ディレクトリ (コンパイラの起動元のディレクトリ)、または共通言語ランタイムのシステム ディレクトリ。 ディレクトリ名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。|  
  
## <a name="remarks"></a>コメント  
 `/libpath`オプションによって参照されるアセンブリの場所を指定する、 [/reference](../../../visual-basic/reference/command-line-compiler/reference.md)オプション。  
  
 コンパイラは、完全に修飾されていないアセンブリ参照を次の順序で検索します。  
  
1.  現在の作業ディレクトリ。 これは、コンパイラを起動したディレクトリです。  
  
2.  共通言語ランタイムのシステム ディレクトリ。  
  
3.  指定したディレクトリ`/libpath`です。  
  
4.  LIB 環境変数によって指定されているディレクトリ。  
  
 `/libpath`オプションが加法; 指定するには、複数の前の値に 1 回追加します。  
  
 使用して`/reference`アセンブリ参照を指定します。  
  
|Visual Studio で/libpath を設定するには、統合開発環境|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.**[参照]** タブをクリックします。<br />3.クリックして、**パスを参照しています.**ボタンをクリックします。<br />4.**参照パス** ダイアログ ボックスで、ディレクトリ名を入力、**フォルダー:**ボックス。<br />5.をクリックして**フォルダーの追加**です。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`.exe ファイルを作成します。 コンパイラは、アセンブリ参照の作業ディレクトリに、c: ドライブのルート ディレクトリ、および c: ドライブのアセンブリを新しいディレクトリに検索します。  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
