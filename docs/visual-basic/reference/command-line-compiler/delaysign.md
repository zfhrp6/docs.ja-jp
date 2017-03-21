---
title: "/delaysign |Microsoft ドキュメント"
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
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: 19
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
ms.openlocfilehash: 59d4ec227286c20b2b4ecf749a91f0c4ee8d25ca
ms.lasthandoff: 03/13/2017

---
# <a name="delaysign"></a>T:System.Reflection.AssemblyDelaySignAttribute
アセンブリに完全に署名するか、部分的に署名するかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 省略可能です。 完全署名されたアセンブリを作成する場合は、`/delaysign-` を使用します。 使用`/delaysign+`かどうかは、署名済みのハッシュのアセンブリと予約のスペースで公開キーを配置します。 既定値は、`/delaysign-` です。  
  
## <a name="remarks"></a>コメント  
 `/delaysign`オプションも何も起こりませんと共に使用しなければ[/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)または[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)します。  
  
 完全署名されたアセンブリを要求すると、コンパイラはマニフェスト (アセンブリ メタデータ) を格納し、秘密キーでそのハッシュに署名するファイルをハッシュします。 結果として得られるデジタル署名は、マニフェストを含むファイルに格納されます。 アセンブリに遅延署名がある場合、コンパイラはいないコンピューティングを署名を後で追加できるように、ファイルに署名が予約領域を格納します。  
  
 たとえばを使用して`/delaysign+`組織内の開発者は、テスト担当者がグローバル アセンブリ キャッシュに登録を使用して、アセンブリの署名のないテスト バージョンを配布できます。 アセンブリに対する作業が完了したら、組織の秘密キーの責任者は、アセンブリを完全署名できます。 この区分は、すべての開発者がアセンブリに作業しながら漏洩から組織の秘密キーを保護します。  
  
 参照してください[の作成と using strong-named Assemblies](https://msdn.microsoft.com/library/xwb8f617)アセンブリへの署名の詳細についてです。  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a>統合開発環境 Visual Studio で/delaysign を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  クリックして、**署名** タブをクリックします。  
  
3.  値を設定、**遅延署名のみ**ボックス。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
