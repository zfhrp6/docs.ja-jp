---
title: "/delaysign | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "delaysign compiler option [Visual Basic]"
  - "/delaysign compiler option [Visual Basic]"
  - "-delaysign compiler option [Visual Basic]"
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# /delaysign
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

アセンブリに完全に署名するか、部分的に署名するかを指定します。  
  
## 構文  
  
```  
/delaysign[+ | -]  
```  
  
## 引数  
 `+` &#124; `-`  
 省略可能です。  完全署名されたアセンブリを作成する場合は、`/delaysign-` を使用します。  アセンブリ内に公開キーを配置し、署名付きハッシュの領域を確保する場合は、`/delaysign+` を使用します。  既定値は `/delaysign-` です。  
  
## 解説  
 `/delaysign` オプションは、[\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) または [\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) と共に使用しなければ無効になります。  
  
 完全署名されたアセンブリを要求すると、コンパイラはマニフェスト \(アセンブリ メタデータ\) を含むファイルをハッシュし、そのハッシュに秘密キーで署名します。  結果として得られるデジタル署名は、マニフェストを含むファイルに格納されます。  アセンブリを遅延署名に設定すると、コンパイラは署名の計算も格納も行いませんが、後で署名を追加できるようにファイルに領域を確保します。  
  
 たとえば `/delaysign+` を使用すると、組織内の開発者が署名のないテスト バージョンのアセンブリを配布し、テスト担当者がそのアセンブリをグローバル アセンブリ キャッシュに登録して使用することができます。  このアセンブリに対する作業が終わったら、組織の秘密キーについて責任を持つ人物が、そのアセンブリに完全署名することができます。  この分離方式を使用すると、すべての開発者がアセンブリに対して作業を行えるようにしつつ、組織の秘密キーを漏洩から保護できます。  
  
 アセンブリに対する署名の詳細については、「[厳密な名前付きアセンブリの作成と使用](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)」を参照してください。  
  
### Visual Studio 統合開発環境で \/delaysign を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **\[署名\]** タブをクリックします。  
  
3.  **\[遅延署名のみ\]** に値を設定します。  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)