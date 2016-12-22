---
title: "/reference (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/reference"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/r compiler option [C#]"
  - "reference compiler option [C#]"
  - "r compiler option [C#]"
  - "/reference compiler option [C#]"
  - "-r compiler option [C#]"
  - "metadata import [C#]"
  - "public type information [C#]"
  - "-reference compiler option [C#]"
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /reference (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/reference** オプションは、指定したファイル内で [public](../../../csharp/language-reference/keywords/public.md) として宣言された型の情報を現在のプロジェクトにインポートするよう、コンパイラに対して指示します。こうすることによって、指定したアセンブリ ファイルのメタデータを参照できます。  
  
## 構文  
  
```  
/reference:[alias=]filename  
/reference:filename  
```  
  
## Arguments  
 `filename`  
 アセンブリ マニフェストを含むファイルの名前。  複数のファイルをインポートするには、ファイルごとに **\/reference** オプションを指定します。  
  
 `alias`  
 \(アセンブリ内のすべての名前空間を包含する\) ルート名前空間を表す有効な C\# 識別子。  
  
## 解説  
 複数のファイルをインポートするには、ファイルごとに **\/reference** オプションを指定します。  
  
 インポートするファイルにはマニフェストが必要です。出力ファイルは、[\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 以外のいずれかの [\/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) オプションを使用してコンパイルしておく必要があります。  
  
 **\/r** は **\/reference** の省略形です。  
  
 アセンブリ マニフェストを含まない出力ファイルからメタデータをインポートするには、[\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) を使用します。  
  
 別のアセンブリ \(アセンブリ B\) を参照するアセンブリ \(アセンブリ A\) を参照するときに、次の状況に該当する場合は、アセンブリ B も参照する必要があります。  
  
-   アセンブリ A で使用する型がアセンブリ B の型を継承しているか、アセンブリ B のインターフェイスを実装している場合。  
  
-   アセンブリ B の戻り値の型やパラメーターの型を持つフィールド、プロパティ、イベント、またはメソッドを呼び出す場合。  
  
 [\/lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) を使用して、1 つ以上のアセンブリ参照があるディレクトリを指定します。  **\/lib** に関するトピックでも、コンパイラがアセンブリを検索するディレクトリについて説明しています。  
  
 モジュールではなくアセンブリ内の型をコンパイラで認識するには、型の解決を強制する必要があります。型の解決を実行するには、たとえば、型のインスタンスを定義します。  アセンブリの型名を解決する方法は他にもあります。たとえば、アセンブリの型を継承すると、コンパイラで型名が認識されます。  
  
 1 つのアセンブリから、同じコンポーネントの 2 種類のバージョンを参照しなければならない場合もあります。  そのためには、ファイルごとに **\/reference** スイッチで alias サブオプションを使用し、2 つのファイルを区別します。  このエイリアスがコンポーネント名の修飾子として使用され、いずれかのファイルのコンポーネントに解決されます。  
  
 既定では、頻繁に使用される .NET Framework アセンブリを参照する csc 応答ファイル \(.rsp\) が使用されます。  コンパイラで csc.rsp を使用しない場合は、[\/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) を使用します。  
  
> [!NOTE]
>  Visual Studio で、**\[参照の追加\]** ダイアログ ボックスを使用します。  詳細については、「[方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)」を参照してください。  Visual Studio 2010 以降のバージョンでは、`/reference` を使用した場合と、**\[参照の追加\]** ダイアログ ボックスを使用した場合の参照の追加で同等の動作を確保するには、追加するアセンブリの **\[相互運用型の埋め込み\]** プロパティを **False** に設定する必要があります。  このプロパティの既定値は **True** です。  
  
## 例  
 [extern エイリアス](../../../csharp/language-reference/keywords/extern-alias.md)機能を使用する方法の例を次に示します。  
  
 このソース ファイルをコンパイルして、あらかじめコンパイルされた `grid.dll` および `grid20.dll` `` からメタデータをインポートします。  この 2 つの DLL には、同じコンポーネントの異なるバージョンがそれぞれ格納されています。エイリアス オプションを付けた 2 つの **\/reference** を使用して、ソース ファイルをコンパイルします。  オプションの指定例を次に示します。  
  
 \/reference:GridV1\=grid.dll and \/reference:GridV2\=grid20.dll  
  
 これにより、外部のエイリアス "GridV1" および "GridV2" が設定され、プログラム内から extern ステートメントで使用できるようになります。  
  
```  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 一度このように設定すれば、コントロール名に GridV1 というプレフィックスを指定することにより、grid.dll から、グリッド コントロールを参照できます。  
  
```  
GridV1::Grid  
```  
  
 また、コントロール名に GridV2 というプレフィックスを指定することにより、grid20.dll から、グリッド コントロールを参照できます。  
  
```  
GridV2::Grid   
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)