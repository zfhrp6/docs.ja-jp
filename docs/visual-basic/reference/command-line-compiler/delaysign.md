---
title: T:System.Reflection.AssemblyDelaySignAttribute
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6c42e351808281d90eafdb6e61a3f1736ef15c9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="delaysign"></a>T:System.Reflection.AssemblyDelaySignAttribute
アセンブリに完全に署名するか、部分的に署名するかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 省略可能です。 完全署名されたアセンブリを作成する場合は、`/delaysign-` を使用します。 使用して`/delaysign+`かどうかは、署名のハッシュのアセンブリと予約のスペースで公開キーを配置します。 既定値は、`/delaysign-` です。  
  
## <a name="remarks"></a>コメント  
 `/delaysign`オプションも何も起こりませんと共に使用しなければ[/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)または[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)です。  
  
 アセンブリに完全に署名するように指定すると、コンパイラはマニフェスト (アセンブリ メタデータ) を含むファイルをハッシュし、秘密キーでそのハッシュに署名します。 結果として得られるデジタル署名は、マニフェストを含むファイルに格納されます。 アセンブリに遅延署名がある場合、コンパイラはないを計算し、署名を後で追加できるように、ファイルに署名が予約領域を格納します。  
  
 たとえばを使用して`/delaysign+`組織内の開発者は、テスト担当者がグローバル アセンブリ キャッシュに登録して使用するアセンブリのバージョンの符号なしのテストを配布できます。 アセンブリでの作業が完了したら、組織の秘密キーの責任者は、アセンブリを完全署名できます。 この区分は、すべての開発者が、アセンブリに作業しながら、情報の漏えいから組織の秘密キーを保護します。  
  
 参照してください[作成と使用](https://msdn.microsoft.com/library/xwb8f617)アセンブリに署名する方法についてです。  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a>Visual Studio で/delaysign を設定するには、統合開発環境  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **[署名]** タブをクリックします。  
  
3.  値を設定、**遅延署名のみ**ボックス。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
