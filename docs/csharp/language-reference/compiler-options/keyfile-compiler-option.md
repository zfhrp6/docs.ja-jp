---
title: "/keyfile (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/keyfile"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/keyfile compiler option [C#]"
  - "-keyfile compiler option [C#]"
  - "keyfile compiler option [C#]"
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# /keyfile (C# Compiler Options)
暗号化キーの格納されたファイル名を指定します。  
  
## 構文  
  
```  
/keyfile:file  
```  
  
## Arguments  
  
|語句|定義|  
|--------|--------|  
|`file`|厳密名キーが格納されたファイルの名前。|  
  
## 解説  
 このオプションを使用すると、コンパイラによって、指定したファイルに格納されている公開キーがアセンブリ マニフェストに対して追加され、最終的なアセンブリが秘密キーで署名されます。  キー ファイルを生成するには、コマンド ラインで「sn \-k `file`」と入力します。  
  
 **\/target:module** を使用してコンパイルすると、キー ファイル名はモジュールに保持され、[\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) でアセンブリをコンパイルするときに作成されるアセンブリに組み込まれます。  
  
 [\/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md) を使用して、暗号に関する情報をコンパイラに渡すこともできます。  部分署名されたアセンブリを作成する場合は、[\/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) を使用します。  
  
 コマンド ライン オプションまたはカスタム属性によって、コンパイル時に \/keyfile と \/keycontainer の両方が同時に指定されると、コンパイラは先にキー コンテナーを処理します。  コンテナーが検出された場合、アセンブリはキー コンテナーの情報で署名されます。  キー コンテナーが見つからない場合、コンパイラは \/keyfile で指定されたファイルを処理します。  成功すると、キー ファイル内の情報を使用して、アセンブリが署名されます。キー情報はキー コンテナーに組み込まれるため \(sn \-i と同じ\)、次回のコンパイルではキー コンテナーが有効になります。  
  
 キー ファイルには、公開キーだけが含まれていることがあります。  
  
 詳細については、「[厳密な名前付きアセンブリの作成と使用](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)」および「[アセンブリへの遅延署名](../Topic/Delay%20Signing%20an%20Assembly.md)」を参照してください。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[署名\]** プロパティ ページをクリックします。  
  
3.  **\[厳密な名前のキー ファイルを選択してください\]** プロパティを変更します。  
  
 このコンパイラ オプションには、<xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A> を使用してプログラムでアクセスできます。  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)