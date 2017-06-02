---
title: "完全修飾型名の指定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アセンブリ [.NET Framework], 名前"
  - "Backus-Naur form"
  - "BNF"
  - "完全修飾型名"
  - "IDENTIFIER"
  - "言語, BNF 文法"
  - "名前 [.NET Framework], アセンブリ"
  - "名前 [.NET Framework], 完全修飾型名"
  - "リフレクション, 完全修飾型名"
  - "特殊文字"
  - "トークン"
  - "型名"
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 完全修飾型名の指定
さまざまなリフレクション操作に対して有効な入力を行うには、型名を指定する必要があります。  完全限定型名は、アセンブリ名指定、名前空間指定、および型名で構成されます。  型名指定は、<xref:System.Type.GetType%2A?displayProperty=fullName>、<xref:System.Reflection.Module.GetType%2A?displayProperty=fullName>、<xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=fullName>、<xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName> などのメソッドで使用されます。  
  
## 型名の Backus\-Naur Form 文法  
 Backus\-Naur form \(BNF\) は、公式言語の構文を定義します。  有効な入力がどのように認識されるかを説明する BNF 構文規則の表を次に示します。  必須要素 \(それ以上省略できない要素\) は、すべて英大文字で示します。  必須ではない要素 \(省略可能な要素\) は、大文字と小文字を組み合わせた文字列、または単一引用符で囲んだ文字列で示します。ただし、単一引用符 \('\) はその構文自体の一部ではありません  パイプ文字 \(&#124;\) は、サブ規則を持つ規則を表します。  
  
|完全限定型名の BNF 文法|  
|--------------------|  
|TypeSpec                          :\=   ReferenceTypeSpec<br /><br /> &#124;     SimpleTypeSpec|  
|ReferenceTypeSpec: SimpleTypeSpec '&\= 「|  
|SimpleTypeSpec                :\=   PointerTypeSpec<br /><br /> &#124;     ArrayTypeSpec<br /><br /> &#124;     TypeName|  
|PointerTypeSpec                :\=   SimpleTypeSpec '\*'|  
|ArrayTypeSpec                  :\=   SimpleTypeSpec '\[ReflectionDimension\]'<br /><br /> &#124;     SimpleTypeSpec '\[ReflectionEmitDimension\]'|  
|ReflectionDimension           :\=   '\*'<br /><br /> &#124;     ReflectionDimension ',' ReflectionDimension<br /><br /> &#124;     NOTOKEN|  
|ReflectionEmitDimension    :\=   '\*'<br /><br /> &#124;     Number '..'数値<br /><br /> &#124;     Number '…'<br /><br /> &#124;     ReflectionDimension ',' ReflectionDimension<br /><br /> &#124;     NOTOKEN|  
|Number                            :\=   \[0\-9\]\+|  
|TypeName                         :\=   NamespaceTypeName<br /><br /> &#124;     NamespaceTypeName ',' AssemblyNameSpec|  
|NamespaceTypeName        :\=   NestedTypeName<br /><br /> &#124;     NamespaceSpec '.'NestedTypeName|  
|NestedTypeName               :\=   IDENTIFIER<br /><br /> &#124;     NestedTypeName '\+' IDENTIFIER|  
|NamespaceSpec                 :\=   IDENTIFIER<br /><br /> &#124;     NamespaceSpec '.'IDENTIFIER|  
|AssemblyNameSpec           :\=   IDENTIFIER<br /><br /> &#124;     IDENTIFIER ',' AssemblyProperties|  
|AssemblyProperties            :\=   AssemblyProperty<br /><br /> &#124;     AssemblyProperties ',' AssemblyProperty|  
|AssemblyProperty              :\=   AssemblyPropertyName '\=' AssemblyPropertyValue|  
  
## 特殊文字の指定  
 型名の IDENTIFIER は、言語の規則によって決定される任意の有効な名前です。  
  
 IDENTIFIER の一部として使用される次のトークンを区切るには、エスケープ文字として円記号 \(\\\) を使用します。  
  
|トークン|説明|  
|----------|--------|  
|\\,|アセンブリの区切り記号|  
|\\\+|入れ子にされた型の区切り記号|  
|\\&|参照型|  
|\\\*|ポインター型|  
|\\\[|配列次元の区切り記号|  
|\\\]|配列次元の区切り記号|  
|\\.|配列指定にピリオドが使用されているときだけ、ピリオドの前に円記号を使用します。  NamespaceSpec 内のピリオドには、円記号は付けません。|  
|\\\\|リテラル文字列として使用する円記号|  
  
 AssemblyNameSpec を除くすべての TypeSpec コンポーネントで、スペースに意味があることに注意してください。  AssemblyNameSpec では、区切り記号 ',' の前のスペースには意味がありますが、区切り記号 ',' 後のスペースは無視されます。  
  
 <xref:System.Type.FullName%2A?displayProperty=fullName> などのリフレクション クラスは、分解された名前を返すため、返された名前を `MyType.GetType(myType.FullName)` のように、<xref:System.Type.GetType%2A> の呼び出しで使用できます。  
  
 たとえば、型の完全限定名を `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly` のように記述できます。  
  
 名前空間が `Ozzy.Out+Back` の場合は、プラス記号の前に円記号が必要です。  円記号がない場合、パーサーは、プラス記号を入れ子になった区切り記号と解釈します。  リフレクションでは、この文字列は、`Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly` として出力されます。  
  
## アセンブリ名の指定  
 アセンブリ名指定で最小限必要な情報は、文字列のアセンブリ名 \(IDENTIFIER\) です。  次の表で示すように、IDENTIFIER の後に、プロパティと値のペアをコンマで区切ったリストを記述できます。  IDENTIFIER の名前付けは、ファイル命名規則に従って行う必要があります。  IDENTIFIER は、大文字\/小文字を区別しません。  
  
|プロパティ名|説明|使用できる値|  
|------------|--------|------------|  
|**Version**|アセンブリのバージョン番号|*Major.Minor.Build.Revision*。ここで、*Major*、*Minor*、*Build*、および *Revision* は 0 ～ 65535 の整数を表します。|  
|**PublicKey**|完全公開キー。|16 進形式の文字列値の完全公開キー。  プライベート アセンブリを明示的に示すには、null 参照 \(Visual Basic では **Nothing**\) を指定します。|  
|**PublicKeyToken**|公開キー トークン \(完全公開キーの 8 バイト ハッシュ\)。|16 進形式の文字列値の公開キー トークン。  プライベート アセンブリを明示的に示すには、null 参照 \(Visual Basic では **Nothing**\) を指定します。|  
|**カルチャ**|アセンブリのカルチャ設定。|RFC\-1766 形式のアセンブリのカルチャ設定。言語に依存しないアセンブリの場合は "neutral"\(非サテライト\)。|  
|**Custom**|カスタムのバイナリ ラージ オブジェクト \(BLOB\)。  これは、現在は[ネイティブ イメージ ジェネレーター \(Ngen\)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) で生成されたアセンブリだけで使用されています。|インストールするアセンブリがネイティブ イメージなので、ネイティブ イメージ キャッシュにインストールすることをアセンブリ キャッシュに通知するために、ネイティブ イメージ ジェネレーターが使用するカスタム文字列。  zap 文字列とも呼ばれます。|  
  
 既定のカルチャ設定を持つ簡易名のアセンブリの **AssemblyName** の例を次に示します。  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 カルチャ設定 "en" の厳密な名前のアセンブリに対する、完全指定の参照の例を次に示します。  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 厳密または単純な名前のアセンブリで条件を満たすことができる、部分指定の **AssemblyName** の例を次に示します。  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 簡易名のアセンブリで条件を満たす必要がある、部分指定の **AssemblyName** の例を次に示します。  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 厳密な名前のアセンブリで条件を満たす必要がある、部分指定の **AssemblyName** の例を次に示します。  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## ポインターの指定  
 SimpleTypeSpec\* は、アンマネージ ポインターを表します。  たとえば、MyType 型へのポインターを取得するには、`Type.GetType("MyType*")` を使用します。  MyType 型へのポインターへのポインターを取得するには、`Type.GetType("MyType**")` を使用します。  
  
## 参照の指定  
 SimpleTypeSpec は & マネージ ポインターまたは参照を表します。  たとえば、MyType 型への参照を取得するには、`Type.GetType("MyType &")` を使用します。  ポインターとは異なり、参照は、1 レベルに限定されることに注意してください。  
  
## 配列の指定  
 BNF 文法では、ReflectionEmitDimension は、<xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=fullName> を使用して取得した不完全な型定義だけに適用されます。  不完全な型定義は、[Reflection.Emit](frlrfSystemReflectionEmit) を使用して構築された <xref:System.Reflection.Emit.TypeBuilder> オブジェクトのうち、<xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=fullName> が呼び出されていないオブジェクトです。  ReflectionDimension を使用すると、完成した任意の型定義、つまり、読み込まれている型を取得できます。  
  
 リフレクションでは、配列のランクを指定することにより、配列にアクセスします。  
  
-   `Type.GetType("MyArray[]")` は、下限 0 の 1 次元配列を取得します。  
  
-   `Type.GetType("MyArray[*]")` は、下限が不明の 1 次元配列を取得します。  
  
-   `Type.GetType("MyArray[][]")` は、2 次元配列の配列を取得します。  
  
-   `Type.GetType("MyArray[*,*]")` および `Type.GetType("MyArray[,]")` は、下限が不明の四角形の 2 次元配列を取得します。  
  
 ランタイムから見ると、`MyArray[] != MyArray[*]` ですが、多次元配列の場合は、この 2 つの表記は同等です。  つまり、`Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` は **true** と評価されます。  
  
 **ModuleBuilder.GetType** では、`MyArray[0..5]` は、サイズが 6 で、下限 0 の 1 次元配列を示します。 `MyArray[4…]` は、サイズが不明で、下限 4 の 1 次元配列を示します。  
  
## 参照  
 <xref:System.Reflection.AssemblyName>   
 <xref:System.Reflection.Emit.ModuleBuilder>   
 <xref:System.Reflection.Emit.TypeBuilder>   
 <xref:System.Type.FullName%2A?displayProperty=fullName>   
 <xref:System.Type.GetType%2A?displayProperty=fullName>   
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName>   
 [型情報の表示](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)