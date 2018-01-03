---
title: "文字列に対する既定のマーシャリング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f8de04f9674e67bf1498fb8f25f2b3c61fec438
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="a7b5b-102">文字列に対する既定のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="a7b5b-102">Default Marshaling for Strings</span></span>
<span data-ttu-id="a7b5b-103"><xref:System.String?displayProperty=nameWithType> と <xref:System.Text.StringBuilder?displayProperty=nameWithType> クラスのマーシャリング動作は類似しています。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>  
  
 <span data-ttu-id="a7b5b-104">文字列は、COM スタイル `BSTR` 型または null で終わる文字列 (null 文字で終わる文字配列) としてマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="a7b5b-105">文字列内の文字は、Unicode (Windows システムでの既定値) または ANSI としてマーシャリングすることができます。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>  
  
 <span data-ttu-id="a7b5b-106">このトピックでは、文字列型のマーシャリングに関する以下の情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-106">This topic provides the following information on marshaling string types:</span></span>  
  
-   [<span data-ttu-id="a7b5b-107">インターフェイスで使用される文字列</span><span class="sxs-lookup"><span data-stu-id="a7b5b-107">Strings Used in Interfaces</span></span>](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [<span data-ttu-id="a7b5b-108">プラットフォーム呼び出しで使用される文字列</span><span class="sxs-lookup"><span data-stu-id="a7b5b-108">Strings Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [<span data-ttu-id="a7b5b-109">構造体で使用される文字列</span><span class="sxs-lookup"><span data-stu-id="a7b5b-109">Strings Used in Structures</span></span>](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [<span data-ttu-id="a7b5b-110">固定長文字列バッファー</span><span class="sxs-lookup"><span data-stu-id="a7b5b-110">Fixed-Length String Buffers</span></span>](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>   
## <a name="strings-used-in-interfaces"></a><span data-ttu-id="a7b5b-111">インターフェイスで使用される文字列</span><span class="sxs-lookup"><span data-stu-id="a7b5b-111">Strings Used in Interfaces</span></span>  
 <span data-ttu-id="a7b5b-112">次の表は、アンマネージ コードへのメソッド引数としてマーシャリングするときの、文字列データ型のマーシャリングのオプションを示しています。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-112">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="a7b5b-113"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性は、COM インターフェイスへの文字列をマーシャリングする <xref:System.Runtime.InteropServices.UnmanagedType> 列挙値を提供します。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-113">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>  
  
|<span data-ttu-id="a7b5b-114">列挙型</span><span class="sxs-lookup"><span data-stu-id="a7b5b-114">Enumeration type</span></span>|<span data-ttu-id="a7b5b-115">アンマネージ形式の説明</span><span class="sxs-lookup"><span data-stu-id="a7b5b-115">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="a7b5b-116">`UnmanagedType.BStr` (既定値)</span><span class="sxs-lookup"><span data-stu-id="a7b5b-116">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="a7b5b-117">長さと Unicode 文字がプレフィックスされた COM スタイル `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-117">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="a7b5b-118">ANSI 文字の null で終わる配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-118">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="a7b5b-119">Unicode 文字の null で終わる配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-119">A pointer to a null-terminated array of Unicode characters.</span></span>|  
  
 <span data-ttu-id="a7b5b-120">この表は文字列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-120">This table applies to strings.</span></span> <span data-ttu-id="a7b5b-121">ただし、<xref:System.Text.StringBuilder> の場合、許可される唯一のオプションは `UnmanagedType.LPStr` と `UnmanagedType.LPWStr`です。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-121">However, for <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>  
  
 <span data-ttu-id="a7b5b-122">以下の例では、`IStringWorker` インターフェイスで宣言された文字列を示します。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-122">The following example shows strings declared in the `IStringWorker` interface.</span></span>  
  
```cpp  
public interface IStringWorker {  
void PassString1(String s);  
void PassString2([MarshalAs(UnmanagedType.BStr)]String s);  
void PassString3([MarshalAs(UnmanagedType.LPStr)]String s);  
void PassString4([MarshalAs(UnmanagedType.LPWStr)]String s);  
void PassStringRef1(ref String s);  
void PassStringRef2([MarshalAs(UnmanagedType.BStr)]ref String s);  
void PassStringRef3([MarshalAs(UnmanagedType.LPStr)]ref String s);  
void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)]ref String s);  
);  
```  
  
 <span data-ttu-id="a7b5b-123">以下の例では、タイプ ライブラリに記述された対応するインターフェイスを示します。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-123">The following example shows the corresponding interface described in a type library.</span></span>  
  
```  
[…]  
interface IStringWorker : IDispatch {  
HRESULT PassString1([in] BSTR s);  
HRESULT PassString2([in] BSTR s);  
HRESULT PassString3([in] LPStr s);  
HRESULT PassString4([in] LPWStr s);  
HRESULT PassStringRef1([in, out] BSTR *s);  
HRESULT PassStringRef2([in, out] BSTR *s);  
HRESULT PassStringRef3([in, out] LPStr *s);  
HRESULT PassStringRef4([in, out] LPWStr *s);  
);  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor5"></a>   
## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="a7b5b-124">プラットフォーム呼び出しで使用される文字列</span><span class="sxs-lookup"><span data-stu-id="a7b5b-124">Strings Used in Platform Invoke</span></span>  
 <span data-ttu-id="a7b5b-125">プラットフォーム呼び出しは、文字列の引数を、.NET Framework 形式 (Unicode) から、プラットフォーム アンマネージ形式に変換してコピーします。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-125">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="a7b5b-126">文字列は不変であり、呼び出しが戻るときに、アンマネージ メモリから元のマネージ メモリにコピーされることはありません。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-126">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>  
  
 <span data-ttu-id="a7b5b-127">次の表は、文字列をプラットフォーム呼び出しのメソッド引数としてマーシャリングする際のマーシャリング オプションをリストしています。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-127">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="a7b5b-128"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性は、文字列をマーシャリングする <xref:System.Runtime.InteropServices.UnmanagedType> 列挙値を提供します。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-128">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>  
  
|<span data-ttu-id="a7b5b-129">列挙型</span><span class="sxs-lookup"><span data-stu-id="a7b5b-129">Enumeration type</span></span>|<span data-ttu-id="a7b5b-130">アンマネージ形式の説明</span><span class="sxs-lookup"><span data-stu-id="a7b5b-130">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="a7b5b-131">長さと ANSI 文字がプレフィックスされた COM スタイル `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-131">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|  
|`UnmanagedType.BStr`|<span data-ttu-id="a7b5b-132">長さと Unicode 文字がプレフィックスされた COM スタイル `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-132">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="a7b5b-133">ANSI 文字の null で終わる配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-133">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="a7b5b-134">プラットフォーム依存文字の null で終わる配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-134">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="a7b5b-135">Unicode 文字の null で終わる配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-135">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.TBStr`|<span data-ttu-id="a7b5b-136">長さとプラットフォーム依存文字がプレフィックスされた COM スタイル `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-136">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|  
|`VBByRefStr`|<span data-ttu-id="a7b5b-137">Visual Basic .NET で、アンマネージ コードの文字列を変更し、結果をマネージ コードに反映できるようにする値。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-137">A value that enables Visual Basic .NET to change a string in unmanaged code, and have the results reflected in managed code.</span></span> <span data-ttu-id="a7b5b-138">この値は、プラットフォーム呼び出しでだけサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-138">This value is supported only for platform invoke.</span></span> <span data-ttu-id="a7b5b-139">これが、`ByVal` 文字列の Visual Basic での既定値です。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-139">This is default value in Visual Basic for `ByVal` strings.</span></span>|  
  
 <span data-ttu-id="a7b5b-140">この表は文字列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-140">This table applies to strings.</span></span> <span data-ttu-id="a7b5b-141">ただし、<xref:System.Text.StringBuilder> の場合、許可される唯一のオプションは `LPStr`、`LPTStr`、および `LPWStr` です。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-141">However, for <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>  
  
 <span data-ttu-id="a7b5b-142">次の型定義は、プラットフォーム呼び出しで `MarshalAsAttribute` を使用するための正しい方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-142">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>  
  
```vb  
Class StringLibAPI      
Public Declare Auto Sub PassLPStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPStr)> s As String)      
Public Declare Auto Sub PassLPWStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPWStr)> s As String)      
Public Declare Auto Sub PassLPTStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPTStr)> s As String)      
Public Declare Auto Sub PassBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.BStr)> s As String)      
Public Declare Auto Sub PassAnsiBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.AnsiBStr)> s As String)      
Public Declare Auto Sub PassTBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.TBStr)> s As String)  
End Class  
```  
  
```csharp  
class StringLibAPI {  
[DllImport("StringLib.Dll")]  
public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPWStr([MarshalAs(UnmanagedType.LPWStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPTStr([MarshalAs(UnmanagedType.LPTStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)]  
String s);  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor2"></a>   
## <a name="strings-used-in-structures"></a><span data-ttu-id="a7b5b-143">構造体で使用される文字列</span><span class="sxs-lookup"><span data-stu-id="a7b5b-143">Strings Used in Structures</span></span>  
 <span data-ttu-id="a7b5b-144">文字列は構造体の有効なメンバーです。ただし、<xref:System.Text.StringBuilder> バッファーは構造体では無効です。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-144">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="a7b5b-145">次の表は、型をフィールドとしてマーシャリングするときの、文字列データ型のマーシャリングのオプションを示しています。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-145">The following table shows the marshaling options for the string data type when the type is marshaled as a field.</span></span> <span data-ttu-id="a7b5b-146"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性は、文字列をフィールドにマーシャリングする <xref:System.Runtime.InteropServices.UnmanagedType> 列挙値を提供します。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-146">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>  
  
|<span data-ttu-id="a7b5b-147">列挙型</span><span class="sxs-lookup"><span data-stu-id="a7b5b-147">Enumeration type</span></span>|<span data-ttu-id="a7b5b-148">アンマネージ形式の説明</span><span class="sxs-lookup"><span data-stu-id="a7b5b-148">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|<span data-ttu-id="a7b5b-149">長さと Unicode 文字がプレフィックスされた COM スタイル `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-149">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="a7b5b-150">ANSI 文字の null で終わる配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-150">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="a7b5b-151">プラットフォーム依存文字の null で終わる配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-151">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="a7b5b-152">Unicode 文字の null で終わる配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-152">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.ByValTStr`|<span data-ttu-id="a7b5b-153">固定長の文字配列。配列の型は、包含構造体の文字セットによって決まります。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-153">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|  
  
 <span data-ttu-id="a7b5b-154">`ByValTStr` 型は、構造体に定義されているインライン固定長文字配列で使用します。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-154">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="a7b5b-155">その他の型は、文字列へのポインターを含む構造体に含まれている文字列参照に適用されます。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-155">Other types apply to string references contained within structures that contain pointers to strings.</span></span>  
  
 <span data-ttu-id="a7b5b-156">包含構造体に適用される <xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性の `CharSet` 引数によって、構造体内の文字列の文字形式が決まります。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-156">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="a7b5b-157">以下の構造体の例には、文字列参照とインライン文字列、そして ANSI、Unicode、およびプラットフォーム依存文字が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-157">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span>  
  
### <a name="type-library-representation"></a><span data-ttu-id="a7b5b-158">タイプ ライブラリの表現</span><span class="sxs-lookup"><span data-stu-id="a7b5b-158">Type Library Representation</span></span>  
  
```  
struct StringInfoA {  
   char *    f1;  
   char      f2[256];  
};  
struct StringInfoW {  
   WCHAR *   f1;  
   WCHAR     f2[256];  
   BSTR      f3;  
};  
struct StringInfoT {  
   TCHAR *   f1;  
   TCHAR     f2[256];  
};  
```  
  
 <span data-ttu-id="a7b5b-159">次のコード例は、<xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を使用して、同一の構造体を複数の異なる形式で定義する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-159">The following code example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to define the same structure in different formats.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Ansi)> _  
Structure StringInfoA  
<MarshalAs(UnmanagedType.LPStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
End Structure  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Unicode)> _  
Structure StringInfoW  
<MarshalAs(UnmanagedType.LPWStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
<MarshalAs(UnmanagedType.BStr)> Public f3 As String  
End Structure  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Auto)> _  
Structure StringInfoT  
<MarshalAs(UnmanagedType.LPTStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Ansi)]  
struct StringInfoA {  
   [MarshalAs(UnmanagedType.LPStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Unicode)]  
struct StringInfoW {  
   [MarshalAs(UnmanagedType.LPWStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
   [MarshalAs(UnmanagedType.BStr)] public String f3;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Auto)]  
struct StringInfoT {  
   [MarshalAs(UnmanagedType.LPTStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor3"></a>   
## <a name="fixed-length-string-buffers"></a><span data-ttu-id="a7b5b-160">固定長文字列バッファー</span><span class="sxs-lookup"><span data-stu-id="a7b5b-160">Fixed-Length String Buffers</span></span>  
 <span data-ttu-id="a7b5b-161">状況によっては、固定長の文字列バッファーを、操作するためにアンマネージ コードに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-161">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="a7b5b-162">この場合、呼び出し先は渡されたバッファーの内容を修正できないので、単に文字列を渡すだけでは不十分です。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-162">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="a7b5b-163">文字列が参照によって渡された場合でも、バッファーを特定のサイズに初期化する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-163">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>  
  
 <span data-ttu-id="a7b5b-164">この解決策は、<xref:System.Text.StringBuilder> バッファーを文字列ではなく引数として渡すことです。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-164">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a string.</span></span> <span data-ttu-id="a7b5b-165">呼び出し先は、`StringBuilder` の容量を超えない範囲で、`StringBuilder` を逆参照したり変更したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-165">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="a7b5b-166">また、固定長に初期化することもできます。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-166">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="a7b5b-167">たとえば、`StringBuilder` バッファーを初期化してその容量を `N` にする場合、マーシャラーは (`N`+1) 文字のサイズのバッファーを提供します。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-167">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="a7b5b-168">+1 は、アンマネージ文字列に null 終了文字があることをしめしています。`StringBuilder` にはそれがありません。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-168">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>  
  
 <span data-ttu-id="a7b5b-169">たとえば、Microsoft Win32 API `GetWindowText` (Windows.h に定義されている) 関数は、固定長の文字バッファーを操作するアンマネージ コードを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-169">For example, the Microsoft Win32 API `GetWindowText` function (defined in Windows.h) is a fixed-length character buffer that must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="a7b5b-170">`LpString` は、呼び出し元が割り当てたサイズ `nMaxCount` のバッファーを示します。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-170">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="a7b5b-171">呼び出し元は、バッファーを割り当てて、`nMaxCount` 引数を割り当てられたバッファーのサイズに設定することが期待されています。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-171">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="a7b5b-172">次のコードは、Windows.h で定義されている `GetWindowText` 関数宣言を示しています。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-172">The following code shows the `GetWindowText` function declaration as defined in Windows.h.</span></span>  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 <span data-ttu-id="a7b5b-173">呼び出し先は、`StringBuilder` の容量を超えない範囲で、`StringBuilder` を逆参照したり変更したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-173">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="a7b5b-174">次のコード例は、`StringBuilder` を固定長に初期化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a7b5b-174">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>  
  
```vb  
Public Class Win32API  
Public Declare Auto Sub GetWindowText Lib "User32.Dll" _  
(h As Integer, s As StringBuilder, nMaxCount As Integer)  
End Class  
Public Class Window  
   Friend h As Integer ' Friend handle to Window.  
   Public Function GetText() As String  
      Dim sb As New StringBuilder(256)  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1)  
   Return sb.ToString()  
   End Function  
End Class  
```  
  
```csharp  
public class Win32API {  
[DllImport("User32.Dll")]  
public static extern void GetWindowText(int h, StringBuilder s,   
int nMaxCount);  
}  
public class Window {  
   internal int h;        // Internal handle to Window.  
   public String GetText() {  
      StringBuilder sb = new StringBuilder(256);  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1);  
   return sb.ToString();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7b5b-175">参照</span><span class="sxs-lookup"><span data-stu-id="a7b5b-175">See Also</span></span>  
 [<span data-ttu-id="a7b5b-176">既定のマーシャリング動作</span><span class="sxs-lookup"><span data-stu-id="a7b5b-176">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)  
 [<span data-ttu-id="a7b5b-177">Blittable 型と非 Blittable 型</span><span class="sxs-lookup"><span data-stu-id="a7b5b-177">Blittable and Non-Blittable Types</span></span>](../../../docs/framework/interop/blittable-and-non-blittable-types.md)  
 [<span data-ttu-id="a7b5b-178">方向属性</span><span class="sxs-lookup"><span data-stu-id="a7b5b-178">Directional Attributes</span></span>](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2)  
 [<span data-ttu-id="a7b5b-179">コピーと固定</span><span class="sxs-lookup"><span data-stu-id="a7b5b-179">Copying and Pinning</span></span>](../../../docs/framework/interop/copying-and-pinning.md)
