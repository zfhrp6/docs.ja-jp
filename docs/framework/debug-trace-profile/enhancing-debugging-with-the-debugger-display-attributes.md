---
title: "Enhancing Debugging with the Debugger Display Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "debugger, display attributes"
  - "DebuggerTypeProxyAttribute attribute"
  - "debugging [.NET Framework], debugger display attributes"
  - "DebuggerDisplayAttribute attribute"
  - "display attributes for debugger"
  - "DebuggerBrowsableAttribute attribute"
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# Enhancing Debugging with the Debugger Display Attributes
デバッガー表示属性を使用すると、開発した型の実行時の動作を指定し、その動作を最もよく理解している開発者が、その型がデバッガーに表示されるときの表示形式を指定することもできます。  さらに、`Target` プロパティを提供するデバッガー表示属性は、ソース コードに関する知識を持たないユーザーがアセンブリ レベルで適用できます。  <xref:System.Diagnostics.DebuggerDisplayAttribute> 属性では、デバッガーの変数ウィンドウでの型やメンバーの表示形式を制御できます。  <xref:System.Diagnostics.DebuggerBrowsableAttribute> 属性では、デバッガーの変数ウィンドウでフィールドやプロパティを表示するかどうか、またその表示形式を決定できます。  <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 属性では、型の代替型つまりプロキシを指定し、デバッガー ウィンドウでの型の表示形式を変更できます。  プロキシ \(代替型\) を指定した変数を表示すると、元の型の代わりにプロキシがデバッガー表示ウィンドウに表示されます。デバッガーの変数ウィンドウには、プロキシ型のパブリック メンバーのみが表示されます。  プライベート メンバーは表示されません。  
  
## DebuggerDisplayAttribute の使用  
 <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> コンストラクターの引数は 1 つです。この引数は、型のインスタンスの値列に表示される文字列です。  この文字列には、中かっこ \({ と }\) を含めることができます。  中かっこで囲まれたテキストは、式として評価されます。  たとえば、次の C\# コードでは、正符号 \(\+\) を選択して `MyHashtable` のインスタンスのデバッガー表示を拡張すると "Count \= 4" が表示されます。  
  
```  
[DebuggerDisplay("Count = {count}")]  
class MyHashtable  
{  
    public int count = 4;  
}  
```  
  
 式で参照されるプロパティに適用されている属性は処理されません。  C\# コンパイラでは、対象型の現在のインスタンスについて、このような参照に暗黙的にのみアクセスできる一般的な式を使用できます。  この式には制限があり、エイリアス、ローカル、またはポインターへはアクセスできません。  C\# コードでは、対象型の現在のインスタンスのみについて、`this` ポインターに暗黙的にアクセスできる一般的な式を中かっこに囲んで使用できます。  
  
 たとえば、C\# オブジェクトにオーバーライドされた `ToString()` がある場合、デバッガーはそのオーバーライドを呼び出し、標準的な `{<typeName>}.` タグ内のピリオド削除ではなくオーバーライドの結果を表示します。そのため、オーバーライドされた `ToString()` がある場合、<xref:System.Diagnostics.DebuggerDisplayAttribute> を使用する必要はありません。  両方を使用すると、<xref:System.Diagnostics.DebuggerDisplayAttribute> 属性が `ToString()` オーバーライドよりも優先されます。  
  
## DebuggerBrowsableAttribute の使用  
 デバッガー ウィンドウに表示されるフィールドやプロパティの表示形式を指定するには、<xref:System.Diagnostics.DebuggerBrowsableAttribute> をフィールドまたはプロパティに適用します。  この属性のコンストラクターは、<xref:System.Diagnostics.DebuggerBrowsableState> 列挙値のいずれかを受け取ります。この列挙値は、次のいずれかの状態を指定します。  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState> は、メンバーがデータ ウィンドウに表示されないことを示します。たとえば、フィールドの <xref:System.Diagnostics.DebuggerBrowsableAttribute> にこの値を使用すると、そのフィールドは階層から削除され、型インスタンスの正符号 \(\+\) をクリックして外側の型を展開しても表示されません。  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState> は、既定で、メンバーは表示され、展開されないことを示します。これが既定の動作です。  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState> は、メンバー自体は表示されず、そのメンバーが配列やコレクションの場合、その内在オブジェクトが表示されることを示します。  
  
> [!NOTE]
>  <xref:System.Diagnostics.DebuggerBrowsableAttribute> は、.NET Framework Version 2.0 の Visual Basic ではサポートされません。  
  
 <xref:System.Diagnostics.DebuggerBrowsableAttribute> を使用して、後続のプロパティがクラスのデバッグ ウィンドウに表示されないようにするコード例を次に示します。  
  
```  
[DebuggerBrowsable(DebuggerBrowsableState.Never)]  
public static string y = "Test String";  
```  
  
## DebuggerTypeProxy の使用  
 型のデバッグ ビューを大幅に変更しても、型自体を変更しないときは、<xref:System.Diagnostics.DebuggerTypeProxyAttribute> 属性を使用します。  <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 属性は、型の表示プロキシを指定して、開発者が型のビューを調整できるようにする場合に使用します。<xref:System.Diagnostics.DebuggerDisplayAttribute> と同様に、この属性はアセンブリ レベルで使用できます。その場合、<xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> プロパティで、プロキシを使用する型を指定します。  この属性は、その適用先の型内で発生する入れ子にされたプライベート型を指定するために使用することをお勧めします。型ビューアーをサポートする式エバリュエーターは、型が表示されるときにこの属性をチェックします。  属性が存在する場合、式エバリュエーターは属性の適用対象の型の代わりに表示プロキシ型を使用します。  
  
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> が存在する場合、デバッガー変数ウィンドウにはプロキシ型のパブリック メンバーのみが表示されます。  プライベート メンバーは表示されません。  データ ウィンドウの動作は、属性拡張ビューによって変更されません。  
  
 パフォーマンスへの不必要な影響を避けるために、表示プロキシの属性は、データ ウィンドウ内の型の横にある正符号 \(\+\) をユーザーがクリックするか、または <xref:System.Diagnostics.DebuggerBrowsableAttribute> 属性を適用することによってオブジェクトが展開されるまで処理されません。  したがって、表示型に属性を適用しないことをお勧めします。  属性は表示型の本体内で適用できるようにします。  
  
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> を使用して、デバッガー表示プロキシとして使用する型を指定するコード例を次に示します。  
  
```  
  
[DebuggerTypeProxy(typeof(HashtableDebugView))]  
class MyHashtable : Hashtable  
{  
    private const string TestString =   
        "This should not appear in the debug window.";  
  
    internal class HashtableDebugView  
    {  
        private Hashtable hashtable;  
        public const string TestStringProxy =   
            "This should appear in the debug window.";  
  
        // The constructor for the type proxy class must have a   
        // constructor that takes the target type as a parameter.  
        public HashtableDebugView(Hashtable hashtable)  
        {  
            this.hashtable = hashtable;  
        }  
    }  
}  
```  
  
## 例  
  
### 説明  
 次のコード例を [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] で表示すると、<xref:System.Diagnostics.DebuggerDisplayAttribute>、<xref:System.Diagnostics.DebuggerBrowsableAttribute>、<xref:System.Diagnostics.DebuggerTypeProxyAttribute> の各属性の適用結果を確認できます。  
  
### コード  
 [!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
 [!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
 [!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]  
  
## 参照  
 <xref:System.Diagnostics.DebuggerDisplayAttribute>   
 <xref:System.Diagnostics.DebuggerBrowsableAttribute>   
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>