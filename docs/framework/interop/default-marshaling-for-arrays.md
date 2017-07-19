---
title: "配列に対する既定のマーシャリング | Microsoft Docs"
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
  - "配列, 相互運用マーシャリング"
  - "相互運用マーシャリング, 配列"
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# 配列に対する既定のマーシャリング
全体がマネージ コードから構成されるアプリケーションでは、共通言語ランタイムは配列型を In\/Out パラメーターとして渡します。  一方、相互運用マーシャラーは、既定では配列を In パラメーターとして渡します。  
  
 [固定による最適化](../../../docs/framework/interop/copying-and-pinning.md)を行う場合、blittable 型の配列は、同一アパートメント内のオブジェクトと対話するときには In\/Out パラメーターとして動作するように見えることがあります。  ただし、コンピューター間のプロキシを生成するときに使用するタイプ ライブラリに後からコードをエクスポートし、そのライブラリを使用してアパートメント間呼び出しをマーシャリングする場合は、その呼び出しの動作が本来の In パラメーターの動作に戻ることがあります。  
  
 本質的に配列は複雑であり、マネージ配列とアンマネージ配列の違いによって、他の非 blittable 型以上の情報が確保されています。  ここでは、配列のマーシャリングに関して次の情報を示します。  
  
-   [マネージ配列](#cpcondefaultmarshalingforarraysanchor1)  
  
-   [アンマネージ配列](#cpcondefaultmarshalingforarraysanchor2)  
  
-   [.NET コードへの配列パラメーターの引き渡し](#cpcondefaultmarshalingforarraysanchor3)  
  
-   [COM への配列の引き渡し](#cpcondefaultmarshalingforarraysanchor4)  
  
<a name="cpcondefaultmarshalingforarraysanchor1"></a>   
## マネージ配列  
 さまざまなマネージ配列型がありますが、<xref:System.Array?displayProperty=fullName> クラスがすべての配列型の基本クラスです。  **System.Array** クラスには、配列のランク、長さ、および下限と上限を決定するプロパティと、配列に対するアクセス、並べ替え、検索、コピー、および作成を行うためのメソッドがあります。  
  
 これらの配列型は動的なので、基本クラス ライブラリでは対応する静的型が定義されていません。  要素の型とランクの各組み合わせを、別個の配列の型と考えると便利です。  したがって、整数の 1 次元配列の型は、倍精度浮動小数点型の 1 次元配列の型とは異なります。  同様に、整数の 2 次元配列は、整数の 1 次元配列とは異なります。  型を比較するときに、配列の上下限は考慮されません。  
  
 特定の要素の型、ランク、および下限を持つ必要があるマネージ配列のすべてのインスタンスを次の表に示します。  
  
|マネージ配列型|要素の型|順位|下限|シグネチャの表記|  
|-------------|----------|--------|--------|--------------|  
|**ELEMENT\_TYPE\_ARRAY**|type で指定します。|rank で指定します。|オプションとして bounds で指定します。|*type* **\[** *n*,*m* **\]**|  
|**ELEMENT\_TYPE\_CLASS**|Unknown|Unknown|Unknown|**System.Array**|  
|**ELEMENT\_TYPE\_SZARRAY**|type で指定します。|1|0|*type* **\[** *n* **\]**|  
  
<a name="cpcondefaultmarshalingforarraysanchor2"></a>   
## アンマネージ配列  
 アンマネージ配列は、COM スタイルのセーフ配列か、または固定長または可変長の C スタイル配列です。  セーフ配列は、関連付けられている配列データの型、ランク、および上下限を共に伝達する自己記述型の配列です。  C スタイルの配列は、下限が 0 で固定され、型が指定されている 1 次元の配列です。  マーシャリング サービスは両方の配列型を制限付きでサポートします。  
  
<a name="cpcondefaultmarshalingforarraysanchor3"></a>   
## .NET コードへの配列パラメーターの引き渡し  
 C スタイルの配列とセーフ配列の両方を、セーフ配列または C スタイル配列として、アンマネージ コードから .NET コードに渡すことができます。  アンマネージ型の値とインポート後の型を次の表に示します。  
  
|アンマネージ型|インポート後の型|  
|-------------|--------------|  
|**SafeArray\(** *Type* **\)**|**ELEMENT\_TYPE\_SZARRAY** **\<** *ConvertedType* **\>**<br /><br /> ランク \= 1、下限 \= 0。  サイズは、マネージ シグネチャで指定されている場合にのみ判明します。  ランク \= 1 または下限 \= 0 ではないセーフ配列は、**SZARRAY** としてマーシャリングできません。|  
|*Type*  **\[\]**|**ELEMENT\_TYPE\_SZARRAY** **\<** *ConvertedType* **\>**<br /><br /> ランク \= 1、下限 \= 0。  サイズは、マネージ シグネチャで指定されている場合にのみ判明します。|  
  
### セーフ配列  
 セーフ配列をタイプ ライブラリから .NET アセンブリにインポートする場合、その配列は既知の型 \(**int** など\) の 1 次元配列に変換されます。  パラメーターに適用されるのと同じ型変換規則が、配列の要素にも適用されます。  たとえば、**BSTR** 型のセーフ配列は文字列のマネージ配列になり、バリアントのセーフ配列はオブジェクトのマネージ配列になります。  **SAFEARRAY** 要素型は、タイプ ライブラリから取り込まれ、<xref:System.Runtime.InteropServices.UnmanagedType> 列挙体の **SAFEARRAY** 値に保存されます。  
  
 セーフ配列のランクと下限はタイプ ライブラリからは特定できないため、ランクは 1 に等しく下限は 0 に等しいと想定されます。  ランクと下限は、[タイプ ライブラリ インポーター \(Tlbimp.exe\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) によって生成されるマネージ シグネチャで定義する必要があります。  実行時にメソッドに渡されるランクが異なる場合には、<xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> がスローされます。  実行時に渡される配列の型が異なる場合には、<xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> がスローされます。  マネージ コードとアンマネージ コードに含まれるセーフ配列の例を次に示します。  
  
 **アンマネージ シグネチャ**  
  
```  
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 **マネージ シグネチャ**  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_I4)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_DATE)> _   
   ar() As DateTime)  
Sub New3(ByRef <MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_BSTR)> _   
   ar() As String)  
  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_I4)] int[] ar) ;  
void New2([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_DATE)]   
   DateTime[] ar);  
void New3([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_BSTR)]   
   ref String[] ar);  
```  
  
 Tlbimp.exe によって生成されたメソッド シグネチャが、**ELEMENT\_TYPE\_SZARRAY** 要素型の代わりに **ELEMENT\_TYPE\_ARRAY** 要素型を指定するように修正されている場合は、多次元のセーフ配列または下限がゼロではないセーフ配列をマネージ コードへとマーシャリングできます。  その代わりに、**\/sysarray** スイッチを指定して Tlbimp.exe を使用すると、すべての配列を <xref:System.Array?displayProperty=fullName> オブジェクトとしてインポートできます。  渡す配列が多次元配列であるとわかっている場合には、Tlbimp.exe によって生成された Microsoft Intermediate Language \(MSIL\) コードを編集してから再コンパイルできます。  MSIL コードの修正方法については、「[ランタイム呼び出し可能ラッパーのカスタマイズ](http://msdn.microsoft.com/ja-jp/4652beaf-77d0-4f37-9687-ca193288c0be)」を参照してください。  
  
### C スタイルの配列  
 C スタイルの配列をタイプ ライブラリから .NET アセンブリにインポートする場合、その配列は **ELEMENT\_TYPE\_SZARRAY** に変換されます。  
  
 配列の要素型は、タイプ ライブラリから判断され、インポート時に維持されます。  パラメーターに適用されるのと同じ変換規則が配列の要素にも適用されます。  たとえば、**LPStr** 型の配列は **String** 型の配列になります。  Tlbimp.exe は配列の要素型を取り込み、<xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性をそのパラメーターに適用します。  
  
 配列のランクは 1 に等しいと想定されます。  ランクが 1 よりも大きい場合、その配列は 1 次元配列として列優先でマーシャリングされます。  下限は常に 0 に等しくなります。  
  
 タイプ ライブラリには固定長または可変長の配列を含めることができます。  しかし、タイプ ライブラリには可変長の配列をマーシャリングするために必要な情報が不足しているため、Tlbimp.exe でインポートできるのは固定長の配列だけです。  固定長の配列の場合、サイズはタイプ ライブラリからインポートされて **MarshalAsAttribute** に取り込まれ、パラメーターに適用されます。  
  
 可変長の配列を含むタイプ ライブラリは、次の例に示すように手動で定義する必要があります。  
  
 **アンマネージ シグネチャ**  
  
```  
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 **マネージ シグネチャ**  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.LPArray, SizeConst=10)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, SizeConst=200)> _  
   ar() As Double)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)> _  
   ar() As String)  
  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.LPArray, SizeConst=10)] int[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray, SizeConst=200)] double[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray,   
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)] String[] ar);  
```  
  
 インターフェイス定義言語 \(IDL: Interface Definition Language\) ソース内の配列に **size\_is** 属性または **length\_is** 属性を適用してサイズをクライアントに伝えることはできますが、MIDL \(Microsoft Interface Definition Language\) コンパイラはこの情報をタイプ ライブラリに反映しません。  サイズがわからない場合、相互運用マーシャリング サービスは配列の要素をマーシャリングできません。  その結果、可変長の配列は参照引数としてインポートされます。  次に例を示します。  
  
 **アンマネージ シグネチャ**  
  
```  
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 **マネージ シグネチャ**  
  
```vb  
Sub New1(ByRef ar As Integer)  
Sub New2(ByRef ar As Double)  
Sub New3(ByRef ar As String)  
  
```  
  
```csharp  
void New1(ref int ar);    
void New2(ref double ar);    
void New3(ref String ar);   
```  
  
 Tlbimp.exe によって生成された Microsoft intermediate language \(MSIL\) コードを編集し、そのコードを再コンパイルすると、マーシャラーに配列のサイズを提供できます。  MSIL コードの修正方法については、「[ランタイム呼び出し可能ラッパーのカスタマイズ](http://msdn.microsoft.com/ja-jp/4652beaf-77d0-4f37-9687-ca193288c0be)」を参照してください。  配列内の要素数を表示するには、次のいずれかの方法によって、マネージ メソッド定義内の配列パラメーターに <xref:System.Runtime.InteropServices.MarshalAsAttribute> 型を適用します。  
  
-   配列内の要素数を含む別のパラメーターを識別します。  パラメーターは位置によって識別されます。最初のパラメーターは 0 番です。  \[Visual Basic\]  
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       <MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,   
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
-   配列のサイズを定数として定義します。  次に例を示します。  
  
    ```vb  
    Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 アンマネージ コードからマネージ コードに配列をマーシャリングする場合、マーシャラーはパラメーターと関連付けられている **MarshalAsAttribute** をチェックして、配列のサイズを判断します。  配列のサイズが指定されていない場合は、1 つの要素だけがマーシャリングされます。  
  
> [!NOTE]
>  **MarshalAsAttribute** は、アンマネージ コードへのマネージ配列のマーシャリングには影響しません。  この方向では、配列のサイズはその配列を調べることで判断できます。  マネージ配列のサブセットをマーシャリングする方法はありません。  
  
 相互運用マーシャラーは **CoTaskMemAlloc** メソッドと **CoTaskMemFree** メソッドを使用して、メモリの割り当てと取得を行います。  アンマネージ コードがメモリを割り当てる場合にも、上のメソッドを使用する必要があります。  
  
<a name="cpcondefaultmarshalingforarraysanchor4"></a>   
## COM への配列の引き渡し  
 すべてのマネージ配列の型をマネージ コードからアンマネージ コードに渡すことができます。  次の表に示すように、配列には、マネージ型および適用される属性に応じて、セーフ配列または C スタイルの配列としてアクセスできます。  
  
|マネージ配列型|エクスポート後の配列|  
|-------------|----------------|  
|**ELEMENT\_TYPE\_SZARRAY** **\<** *type* **\>**|<xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray\(** *type* **\)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> 型がシグネチャに設定されます。  ランクは常に 1 で、下限は常に 0 です。  サイズは常に実行時に判明します。|  
|**ELEMENT\_TYPE\_ARRAY** **\<** *type* **\>** **\<** *rank* **\>**\[**\<** *bounds* **\>**\]|**UnmanagedType.SafeArray\(** *type* **\)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> 型、ランク、上下限がシグネチャに設定されます。  サイズは常に実行時に判明します。|  
|**ELEMENT\_TYPE\_CLASS** **\<**<xref:System.Array?displayProperty=fullName>**\>**|**UT\_Interface**<br /><br /> **UnmanagedType.SafeArray\(** *type* **\)**<br /><br /> 型、ランク、境界、およびサイズは常に実行時に判明します。|  
  
 LPSTR または LPWSTR を含む構造体の配列に関して、OLE オートメーションには制限があります。  そのため、**String** フィールドは **UnmanagedType.BSTR** としてマーシャリングする必要があります。  この操作を行わない場合、例外がスローされます。  
  
### ELEMENT\_TYPE\_SZARRAY  
 **ELEMENT\_TYPE\_SZARRAY** パラメーター \(1 次元配列\) を含むメソッドを .NET アセンブリからタイプ ライブラリにエクスポートする場合、この配列パラメーターは特定の型の **SAFEARRAY** に変換されます。  同じ変換規則が配列の要素型にも適用されます。  マネージ配列の内容は、自動的にマネージ メモリから **SAFEARRAY** へとコピーされます。  次に例を示します。  
  
#### マネージ シグネチャ  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### アンマネージ シグネチャ  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 セーフ配列のランクは常に 1 で、下限は常に 0 です。  サイズは、渡されるマネージ配列のサイズによって実行時に決定されます。  
  
 また、<xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を使用すると、この配列を C スタイルの配列としてもマーシャリングできます。  次に例を示します。  
  
#### マネージ シグネチャ  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As Long, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]   
   long [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]   
   String [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, ArraySubType=   
   UnmanagedType.LPStr, SizeParamIndex=1)]   
   String [] ar, int size );  
```  
  
#### アンマネージ シグネチャ  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 マーシャラーは配列をマーシャリングするために必要な長さ情報を保持しますが、通常は、配列の長さは、呼び出し先に長さを伝えるために個別の引数として渡されます。  
  
### ELEMENT\_TYPE\_ARRAY  
 **ELEMENT\_TYPE\_ARRAY** パラメーターを含むメソッドを .NET アセンブリからタイプ ライブラリにエクスポートする場合、その配列パラメーターは特定の型の **SAFEARRAY** に変換されます。  マネージ配列の内容は、自動的にマネージ メモリから **SAFEARRAY** へとコピーされます。  次に例を示します。  
  
#### マネージ シグネチャ  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### アンマネージ シグネチャ  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 セーフ配列のランク、サイズ、および上下限は、マネージ配列の特徴によって実行時に決定されます。  
  
 また、<xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を適用すると、この配列を C スタイルの配列としてもマーシャリングできます。  次に例を示します。  
  
#### マネージ シグネチャ  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex:=1)> _  
   ar(,) As Long, size As Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, _  
   ArraySubType:=UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar(,) As String, size As Integer)  
  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex=1)]   
   long [,] ar, int size );  
void New([MarshalAs(UnmanagedType.LPARRAY,   
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex=1)]   
   String [,] ar, int size );  
```  
  
#### アンマネージ シグネチャ  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 入れ子の配列はマーシャリングできません。  たとえば、次のシグネチャを[タイプ ライブラリ エクスポーター \(Tlbexp.exe\)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) によってエクスポートするとエラーが発生します。  
  
#### マネージ シグネチャ  
  
```vb  
Sub [New](ar()()() As Long)  
  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### ELEMENT\_TYPE\_CLASS \<System.Array\>  
 <xref:System.Array?displayProperty=fullName> パラメーターを含むメソッドを .NET アセンブリからタイプ ライブラリにエクスポートする場合、この配列パラメーターは **\_Array** インターフェイスに変換されます。  このマネージ配列の内容には、**\_Array** インターフェイスのメソッドとプロパティを通じてだけアクセスできます。  また、<xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を使用すると、**System.Array** を **SAFEARRAY** としてもマーシャリングできます。  セーフ配列としてマーシャリングした場合、配列の要素はバリアントとしてマーシャリングされます。  次に例を示します。  
  
#### マネージ シグネチャ  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### アンマネージ シグネチャ  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### 構造体の中の配列  
 アンマネージ構造体には配列を埋め込むことができます。  既定では、埋め込まれた配列フィールドは、SAFEARRAY としてマーシャリングされます。  次の例では、`s1` が構造体の中に直接割り当てられている配列です。  
  
#### アンマネージ表現  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 配列を [UnmanagedType.ByValArray](frlrfSystemRuntimeInteropServicesUnmanagedTypeClassTopic) としてマーシャリングできますが、そのためには [MarshalAsAttribute.SizeConst](frlrfSystemRuntimeInteropServicesMarshalAsAttributeClassTopic) フィールドを設定する必要があります。  サイズは定数としてだけ設定できます。  次のコードでは、 `MyStruct` に対応するマネージ定義を示しています。  
  
```vb  
Public Structure <StructLayout(LayoutKind.Sequential)> MyStruct  
   Public <MarshalAs(UnmanagedType.ByValArray, SizeConst := 128)> _  
     s1() As Short  
End Structure  
  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MyStruct {  
   [MarshalAs(UnmanagedType.ByValArray, SizeConst=128)] public short[] s1;  
}  
```  
  
## 参照  
 [既定のマーシャリングの動作](../../../docs/framework/interop/default-marshaling-behavior.md)   
 [Blittable 型と非 Blittable 型](../../../docs/framework/interop/blittable-and-non-blittable-types.md)   
 [Directional Attributes](http://msdn.microsoft.com/ja-jp/241ac5b5-928e-4969-8f58-1dbc048f9ea2)   
 [コピーと固定](../../../docs/framework/interop/copying-and-pinning.md)