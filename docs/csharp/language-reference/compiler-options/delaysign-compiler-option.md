---
title: "/delaysign (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/delaysign"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-delaysign compiler option [C#]"
  - "delaysign compiler option [C#]"
  - "/delaysign compiler option [C#]"
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# /delaysign (C# Compiler Options)
このオプションを使用すると、デジタル署名を後で追加できるように、コンパイラは出力ファイルに署名用のスペースを予約します。  
  
## 構文  
  
```  
/delaysign[ + | - ]  
```  
  
## Arguments  
 `+` &#124; `-`  
 完全署名されたアセンブリを作成する場合は、**\/delaysign\-** を使用します。  アセンブリに公開キーだけを含める場合は、**\/delaysign\+** を使います。  既定値は、**\/delaysign\-** です。  
  
## 解説  
 **\/delaysign** オプションは、[\/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) または [\/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md) と共に使用した場合にだけ有効です。  
  
 完全署名されたアセンブリを要求すると、コンパイラはマニフェスト \(アセンブリ メタデータ\) を含むファイルをハッシュし、そのハッシュに秘密キーで署名します。  結果として得られるデジタル署名は、マニフェストを含むファイルに格納されます。  アセンブリを遅延署名に設定すると、コンパイラは署名の計算も格納も行いませんが、後で署名を追加できるようにファイルに領域を確保します。  
  
 たとえば、**\/delaysign\+** を指定すると、テスト時にはアセンブリをグローバル キャッシュに格納できます。  テスト後に、[アセンブリ リンカー](../Topic/Al.exe%20\(Assembly%20Linker\).md) ユーティリティを使用してアセンブリに秘密キーを追加することにより、そのアセンブリに完全署名できます。  
  
 詳細については、「[厳密な名前付きアセンブリの作成と使用](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)」および「[アセンブリへの遅延署名](../Topic/Delay%20Signing%20an%20Assembly.md)」を参照してください。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[遅延署名のみ\]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.DelaySign%2A>」を参照してください。  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)