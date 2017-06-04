---
title: "オブジェクトに対する既定のマーシャリング | Microsoft Docs"
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
  - "相互運用マーシャリング, オブジェクト"
  - "オブジェクト, 相互運用マーシャリング"
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# オブジェクトに対する既定のマーシャリング
<xref:System.Object?displayProperty=fullName> 型として指定されているパラメーターおよびフィールドを、次のいずれかの型としてアンマネージ コードに公開できます。  
  
-   そのオブジェクトがパラメーターの場合にはバリアント。  
  
-   そのオブジェクトが構造体フィールドの場合にはインターフェイス。  
  
 COM 相互運用機能だけがオブジェクト型のマーシャリングをサポートします。  既定の動作では、オブジェクトは COM バリアントへとマーシャリングされます。  これらの規則は **Object** 型だけに適用され、**Object** クラスから派生した、厳密に型指定されたオブジェクトには適用されません。  
  
 ここでは、オブジェクト型のマーシャリングに関する追加情報を示します。  
  
-   [マーシャリング オプション](#cpcondefaultmarshalingforobjectsanchor7)  
  
-   [インターフェイスへのオブジェクトのマーシャリング](#cpcondefaultmarshalingforobjectsanchor2)  
  
-   [バリアントへのオブジェクトのマーシャリング](#cpcondefaultmarshalingforobjectsanchor3)  
  
-   [オブジェクトへのバリアントのマーシャリング](#cpcondefaultmarshalingforobjectsanchor4)  
  
-   [ByRef バリアントのマーシャリング](#cpcondefaultmarshalingforobjectsanchor6)  
  
<a name="cpcondefaultmarshalingforobjectsanchor7"></a>   
## マーシャリング オプション  
 **Object** データ型に対するマーシャリング オプションを次の表に示します。  <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性は、オブジェクトをマーシャリングするための <xref:System.Runtime.InteropServices.UnmanagedType> 列挙値をいくつか提供します。  
  
|列挙型|アンマネージ表現の説明|  
|---------|-----------------|  
|**UnmanagedType.Struct**<br /><br /> \(パラメーターの既定値\)|COM スタイルのバリアント。|  
|**UnmanagedType.Interface**|可能な場合は **IDispatch** インターフェイス。それ以外の場合は **IUnknown** インターフェイス。|  
|**UnmanagedType.IUnknown**<br /><br /> \(フィールドの既定値\)|**IUnknown** インターフェイス。|  
|**UnmanagedType.IDispatch**|**IDispatch** インターフェイス。|  
  
 `MarshalObject` のマネージ インターフェイス定義を次の例に示します。  
  
```vb  
Interface MarshalObject  
   Sub SetVariant(o As Object)  
   Sub SetVariantRef(ByRef o As Object)  
   Function GetVariant() As Object  
  
   Sub SetIDispatch( <MarshalAs(UnmanagedType.IDispatch)> o As Object)  
   Sub SetIDispatchRef(ByRef <MarshalAs(UnmanagedType.IDispatch)> o _  
      As Object)  
   Function GetIDispatch() As <MarshalAs(UnmanagedType.IDispatch)> Object  
   Sub SetIUnknown( <MarshalAs(UnmanagedType.IUnknown)> o As Object)  
   Sub SetIUnknownRef(ByRef <MarshalAs(UnmanagedType.IUnknown)> o _  
      As Object)  
   Function GetIUnknown() As <MarshalAs(UnmanagedType.IUnknown)> Object  
End Interface  
  
```  
  
```csharp  
interface MarshalObject {  
   void SetVariant(Object o);  
   void SetVariantRef(ref Object o);  
   Object GetVariant();  
  
   void SetIDispatch ([MarshalAs(UnmanagedType.IDispatch)]Object o);  
   void SetIDispatchRef([MarshalAs(UnmanagedType.IDispatch)]ref Object o);  
   [MarshalAs(UnmanagedType.IDispatch)] Object GetIDispatch();  
   void SetIUnknown ([MarshalAs(UnmanagedType.IUnknown)]Object o);  
   void SetIUnknownRef([MarshalAs(UnmanagedType.IUnknown)]ref Object o);  
   [MarshalAs(UnmanagedType.IUnknown)] Object GetIUnknown();  
}  
```  
  
 `MarshalObject` インターフェイスをタイプ ライブラリにエクスポートするコード例を次に示します。  
  
```  
interface MarshalObject {  
   HRESULT SetVariant([in] VARIANT o);  
   HRESULT SetVariantRef([in,out] VARIANT *o);  
   HRESULT GetVariant([out,retval] VARIANT *o)   
   HRESULT SetIDispatch([in] IDispatch *o);  
   HRESULT SetIDispatchRef([in,out] IDispatch **o);  
   HRESULT GetIDispatch([out,retval] IDispatch **o)   
   HRESULT SetIUnknown([in] IUnknown *o);  
   HRESULT SetIUnknownRef([in,out] IUnknown **o);  
   HRESULT GetIUnknown([out,retval] IUnknown **o)   
}  
```  
  
> [!NOTE]
>  相互運用マーシャラーは、バリアント内に割り当てられたオブジェクトがある場合は、呼び出しの後で自動的にそのオブジェクトを解放します。  
  
 書式指定された値型を次の例に示します。  
  
```vb  
Public Structure ObjectHolder  
   Dim o1 As Object  
   <MarshalAs(UnmanagedType.IDispatch)> Public o2 As Object  
End Structure  
  
```  
  
```csharp  
public struct ObjectHolder {  
   Object o1;  
   [MarshalAs(UnmanagedType.IDispatch)]public Object o2;  
}  
```  
  
 書式指定された型をタイプ ライブラリにエクスポートするコード例を次に示します。  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
<a name="cpcondefaultmarshalingforobjectsanchor2"></a>   
## インターフェイスへのオブジェクトのマーシャリング  
 オブジェクトをインターフェイスとして COM に公開する場合、そのインターフェイスはマネージ型 <xref:System.Object> 用のクラス インターフェイス \(**\_Object** インターフェイス\) です。  このインターフェイスは、結果のタイプ ライブラリでは、**IDispatch** \([UnmanagedType.IDispatch](frlrfSystemRuntimeInteropServicesUnmanagedTypeClassTopic)\) 型または **IUnknown** \(**UnmanagedType.IUnknown**\) 型として指定されます。  COM クライアントは、マネージ クラスのメンバー、または派生クラスによって実装されるメンバーを **\_Object** インターフェイス経由で動的に呼び出すことができます。  クライアントは **QueryInterface** を呼び出して、マネージ型によって明示的に実装された他の任意のインターフェイスも取得できます。  
  
<a name="cpcondefaultmarshalingforobjectsanchor3"></a>   
## バリアントへのオブジェクトのマーシャリング  
 オブジェクトをバリアントへとマーシャリングする場合、内部バリアント型は次の規則に従って実行時に決定されます。  
  
-   オブジェクト参照が null \(Visual Basic では **Nothing**\) の場合、オブジェクトは **VT\_EMPTY** 型のバリアントへとマーシャリングされます。  
  
-   オブジェクトが、次の表に列挙されるいずれかの型のインスタンスである場合、結果として生成されるバリアント型は、表内に示されている、マーシャラーに組み込みの規則によって決定されます。  
  
-   マーシャリングの動作を明示的に制御する必要があるその他のオブジェクトは、<xref:System.IConvertible> インターフェイスを実装できます。  その場合、バリアントの型は <xref:System.IConvertible.GetTypeCode%2A?displayProperty=fullName> メソッドから返される型コードによって決定されます。  それ以外の場合、オブジェクトは **VT\_UNKNOWN** 型のバリアントとしてマーシャリングされます。  
  
### バリアントへのシステム型のマーシャリング  
 マネージ オブジェクト型、および対応する COM バリアント型を次の表に示します。  これらの型は、呼び出されるメソッドのシグネチャが <xref:System.Object?displayProperty=fullName> 型の場合に限って変換されます。  
  
|オブジェクト型|COM バリアント型|  
|-------------|----------------|  
|null オブジェクト参照 \(Visual Basic では **Nothing**\)。|**VT\_EMPTY**|  
|<xref:System.DBNull?displayProperty=fullName>|**VT\_NULL**|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=fullName>|**VT\_ERROR**|  
|<xref:System.Reflection.Missing?displayProperty=fullName>|**VT\_ERROR** と **E\_PARAMNOTFOUND**|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=fullName>|**VT\_DISPATCH**|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=fullName>|**VT\_UNKNOWN**|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=fullName>|**VT\_CY**|  
|<xref:System.Boolean?displayProperty=fullName>|**VT\_BOOL**|  
|<xref:System.SByte?displayProperty=fullName>|**VT\_I1**|  
|<xref:System.Byte?displayProperty=fullName>|**VT\_UI1**|  
|<xref:System.Int16?displayProperty=fullName>|**VT\_I2**|  
|<xref:System.UInt16?displayProperty=fullName>|**VT\_UI2**|  
|<xref:System.Int32?displayProperty=fullName>|**VT\_I4**|  
|<xref:System.UInt32?displayProperty=fullName>|**VT\_UI4**|  
|<xref:System.Int64?displayProperty=fullName>|**VT\_I8**|  
|<xref:System.UInt64?displayProperty=fullName>|**VT\_UI8**|  
|<xref:System.Single?displayProperty=fullName>|**VT\_R4**|  
|<xref:System.Double?displayProperty=fullName>|**VT\_R8**|  
|<xref:System.Decimal?displayProperty=fullName>|**VT\_DECIMAL**|  
|<xref:System.DateTime?displayProperty=fullName>|**VT\_DATE**|  
|<xref:System.String?displayProperty=fullName>|**VT\_BSTR**|  
|<xref:System.IntPtr?displayProperty=fullName>|**VT\_INT**|  
|<xref:System.UIntPtr?displayProperty=fullName>|**VT\_UINT**|  
|<xref:System.Array?displayProperty=fullName>|**VT\_ARRAY**|  
  
 上の例で定義した `MarshalObject` インターフェイスを使用して、次のコード例では各種の型のバリアントを COM サーバーに渡す方法を示します。  
  
```vb  
Dim mo As New MarshalObject()  
mo.SetVariant(Nothing)         ' Marshal as variant of type VT_EMPTY.  
mo.SetVariant(System.DBNull.Value) ' Marshal as variant of type VT_NULL.  
mo.SetVariant(CInt(27))        ' Marshal as variant of type VT_I2.  
mo.SetVariant(CLng(27))        ' Marshal as variant of type VT_I4.  
mo.SetVariant(CSng(27.0))      ' Marshal as variant of type VT_R4.  
mo.SetVariant(CDbl(27.0))      ' Marshal as variant of type VT_R8.  
  
```  
  
```csharp  
MarshalObject mo = new MarshalObject();  
mo.SetVariant(null);            // Marshal as variant of type VT_EMPTY.  
mo.SetVariant(System.DBNull.Value); // Marshal as variant of type VT_NULL.  
mo.SetVariant((int)27);          // Marshal as variant of type VT_I2.  
mo.SetVariant((long)27);          // Marshal as variant of type VT_I4.  
mo.SetVariant((single)27.0);   // Marshal as variant of type VT_R4.  
mo.SetVariant((double)27.0);   // Marshal as variant of type VT_R8.  
```  
  
 <xref:System.Runtime.InteropServices.ErrorWrapper>、<xref:System.Runtime.InteropServices.DispatchWrapper>、<xref:System.Runtime.InteropServices.UnknownWrapper>、<xref:System.Runtime.InteropServices.CurrencyWrapper> などのラッパー クラスを使用すると、対応するマネージ型を持たない COM 型をマーシャリングできます。  これらのラッパーを使用して各種の型のバリアントを COM サーバーに渡す方法を次のコード例に示します。  
  
```vb  
Imports System.Runtime.InteropServices  
' Pass inew as a variant of type VT_UNKNOWN interface.  
mo.SetVariant(New UnknownWrapper(inew))  
' Pass inew as a variant of type VT_DISPATCH interface.  
mo.SetVariant(New DispatchWrapper(inew))  
' Pass a value as a variant of type VT_ERROR interface.  
mo.SetVariant(New ErrorWrapper(&H80054002))  
' Pass a value as a variant of type VT_CURRENCY interface.  
mo.SetVariant(New CurrencyWrapper(New Decimal(5.25)))  
  
```  
  
```csharp  
using System.Runtime.InteropServices;  
// Pass inew as a variant of type VT_UNKNOWN interface.  
mo.SetVariant(new UnknownWrapper(inew));  
// Pass inew as a variant of type VT_DISPATCH interface.  
mo.SetVariant(new DispatchWrapper(inew));  
// Pass a value as a variant of type VT_ERROR interface.  
mo.SetVariant(new ErrorWrapper(0x80054002));  
// Pass a value as a variant of type VT_CURRENCY interface.  
mo.SetVariant(new CurrencyWrapper(new Decimal(5.25)));  
```  
  
 ラッパー クラスは、<xref:System.Runtime.InteropServices> 名前空間で定義されます。  
  
### バリアントへの IConvertible インターフェイスのマーシャリング  
 上のセクションで列挙した以外の型は、<xref:System.IConvertible> インターフェイスを実装することにより、型のマーシャリング方法を制御できます。  オブジェクトが **IConvertible** インターフェイスを実装する場合、その COM バリアント型は <xref:System.IConvertible.GetTypeCode%2A?displayProperty=fullName> メソッドから返された <xref:System.TypeCode> 列挙体の値によって実行時に決定されます。  
  
 **TypeCode** 列挙体に対して有効な値、およびそれぞれの値に対応する COM バリアント型を次の表に示します。  
  
|TypeCode|COM バリアント型|  
|--------------|----------------|  
|**TypeCode.Empty**|**VT\_EMPTY**|  
|**TypeCode.Object**|**VT\_UNKNOWN**|  
|**TypeCode.DBNull**|**VT\_NULL**|  
|**TypeCode.Boolean**|**VT\_BOOL**|  
|**TypeCode.Char**|**VT\_UI2**|  
|**TypeCode.Sbyte**|**VT\_I1**|  
|**TypeCode.Byte**|**VT\_UI1**|  
|**TypeCode.Int16**|**VT\_I2**|  
|**TypeCode.UInt16**|**VT\_UI2**|  
|**TypeCode.Int32**|**VT\_I4**|  
|**TypeCode.UInt32**|**VT\_UI4**|  
|**TypeCode.Int64**|**VT\_I8**|  
|**TypeCode.UInt64**|**VT\_UI8**|  
|**TypeCode.Single**|**VT\_R4**|  
|**TypeCode.Double**|**VT\_R8**|  
|**TypeCode.Decimal**|**VT\_DECIMAL**|  
|**TypeCode.DateTime**|**VT\_DATE**|  
|**TypeCode.String**|**VT\_BSTR**|  
|サポートされていません。|**VT\_INT**|  
|サポートされていません。|**VT\_UINT**|  
|サポートされていません。|**VT\_ARRAY**|  
|サポートされていません。|**VT\_RECORD**|  
|サポートされていません。|**VT\_CY**|  
|サポートされていません。|**VT\_VARIANT**|  
  
 COM バリアントの値は、**IConvertible.To** *Type* インターフェイスを呼び出すことで判断されます。**To** *Type* は、**IConvertible.GetTypeCode** から返された型に対応する変換ルーチンです。  たとえば、**IConvertible.GetTypeCode** から **TypeCode.Double** を返すオブジェクトは、**VT\_R8** 型の COM バリアントとしてマーシャリングされます。  バリアントの値は、**IConvertible** インターフェイスにキャストし、<xref:System.IConvertible.ToDouble%2A> メソッドを呼び出すことで取得でき、その COM バリアントの **dblVal** フィールド内に格納されます。  
  
<a name="cpcondefaultmarshalingforobjectsanchor4"></a>   
## オブジェクトへのバリアントのマーシャリング  
 バリアントをオブジェクトへとマーシャリングする場合、マーシャリングされるバリアントの型、および場合によっては値が、生成されるオブジェクトの型を決定します。  各バリアント型、および対応するオブジェクト型を次の表に示します。オブジェクト型はバリアントが COM から .NET Framework に渡されるときにマーシャラーによって作成されます。  
  
|COM バリアント型|オブジェクト型|  
|----------------|-------------|  
|**VT\_EMPTY**|null オブジェクト参照 \(Visual Basic では **Nothing**\)。|  
|**VT\_NULL**|<xref:System.DBNull?displayProperty=fullName>|  
|**VT\_DISPATCH**|**System.\_\_ComObject** または \(pdispVal \=\= null\) の場合は null。|  
|**VT\_UNKNOWN**|**System.\_\_ComObject** または \(punkVal \=\= null\) の場合は null。|  
|**VT\_ERROR**|<xref:System.UInt32?displayProperty=fullName>|  
|**VT\_BOOL**|<xref:System.Boolean?displayProperty=fullName>|  
|**VT\_I1**|<xref:System.SByte?displayProperty=fullName>|  
|**VT\_UI1**|<xref:System.Byte?displayProperty=fullName>|  
|**VT\_I2**|<xref:System.Int16?displayProperty=fullName>|  
|**VT\_UI2**|<xref:System.UInt16?displayProperty=fullName>|  
|**VT\_I4**|<xref:System.Int32?displayProperty=fullName>|  
|**VT\_UI4**|<xref:System.UInt32?displayProperty=fullName>|  
|**VT\_I8**|<xref:System.Int64?displayProperty=fullName>|  
|**VT\_UI8**|<xref:System.UInt64?displayProperty=fullName>|  
|**VT\_R4**|<xref:System.Single?displayProperty=fullName>|  
|**VT\_R8**|<xref:System.Double?displayProperty=fullName>|  
|**VT\_DECIMAL**|<xref:System.Decimal?displayProperty=fullName>|  
|**VT\_DATE**|<xref:System.DateTime?displayProperty=fullName>|  
|**VT\_BSTR**|<xref:System.String?displayProperty=fullName>|  
|**VT\_INT**|<xref:System.Int32?displayProperty=fullName>|  
|**VT\_UINT**|<xref:System.UInt32?displayProperty=fullName>|  
|**VT\_ARRAY** &#124; **VT\_\***|<xref:System.Array?displayProperty=fullName>|  
|**VT\_CY**|<xref:System.Decimal?displayProperty=fullName>|  
|**VT\_RECORD**|対応するボックス化された値型。|  
|**VT\_VARIANT**|サポートされていません。|  
  
 COM からマネージ コードに渡された後で COM に返されるバリアント型が、呼び出し中に同じバリアント型を維持しないことがあります。  **VT\_DISPATCH** 型のバリアントが COM から .NET Framework に渡されるときに、何が起こるのかを検討してみます。  マーシャリング時に、バリアントは <xref:System.Object?displayProperty=fullName> に変換されます。  次に **Object** が COM に返される場合には、**VT\_UNKNOWN** 型のバリアントにマーシャリングされます。  オブジェクトをマネージ コードから COM へとマーシャリングするときに、生成されるバリアントの型が、最初にオブジェクトを生成するときに使用したバリアントの型と同じになる保証はありません。  
  
<a name="cpcondefaultmarshalingforobjectsanchor6"></a>   
## ByRef バリアントのマーシャリング  
 バリアント自体を値渡しまたは参照渡しすることはできますが、**VT\_BYREF** フラグを任意のバリアント型と併用した場合は、そのバリアントの内容を値渡しではなく参照渡しすることを指定できます。  バリアントの参照渡しによるマーシャリングと、**VT\_BYREF** フラグの設定によるバリアントのマーシャリングとの違いは微妙です。  その違いを次の図で明確にします。  
  
 ![スタック上で渡されるバリアント](../../../docs/framework/interop/media/interopvariant.gif "interopvariant")  
値渡しされるバリアントと参照渡しされるバリアント  
  
 **オブジェクトとバリアントを値渡しによってマーシャリングする場合の既定の動作**  
  
-   オブジェクトをマネージ コードから COM に渡す場合、そのオブジェクトの内容は、「[バリアントへのオブジェクトのマーシャリング](#cpcondefaultmarshalingforobjectsanchor3)」で定義される規則に従ってマーシャラーによって作成される新しいバリアントにコピーされます。  アンマネージ側でバリアントに対して行われた変更の内容は、呼び出しから制御が返されるときに、元のオブジェクトには反映されません。  
  
-   バリアントを COM からマネージ コードに渡す場合、そのバリアントの内容は、「[オブジェクトへのバリアントのマーシャリング](#cpcondefaultmarshalingforobjectsanchor4)」で定義される規則に従って新規作成されるオブジェクトにコピーされます。  マネージ側でオブジェクトに対して行われた変更の内容は、呼び出しから制御が返されるときに、元のバリアントには反映されません。  
  
 **オブジェクトとバリアントを参照渡しによってマーシャリングする場合の既定の動作**  
  
 変更内容を呼び出し元にも反映させるためには、パラメーターを参照渡しする必要があります。  たとえば、C\# でキーワード **ref** \(Visual Basic マネージ コードの場合は **ByRef**\) を使用すると、パラメーターを参照渡しできます。  COM の場合は、参照パラメーターを渡すには、**variant \*** などのポインターを使用します。  
  
-   オブジェクトを COM に参照渡しする場合、マーシャラーは呼び出しを実行する前に新しいバリアントを作成し、オブジェクト参照の内容をそのバリアントにコピーします。  このバリアントはアンマネージ関数に渡されます。ここで、バリアントの内容を自由に変更できます。  呼び出しから制御が返されるときに、アンマネージ側でバリアントが変更されている場合には、その内容が元のオブジェクトに反映されます。  バリアントの型が、呼び出しに渡されたバリアントの型と異なる場合、変更内容は別の型を持つオブジェクトに反映されます。  つまり、呼び出しに渡したオブジェクトの型が、呼び出しから返されるオブジェクトの型と異なることがあります。  
  
-   バリアントをマネージ コードに参照渡しする場合、マーシャラーは呼び出しを実行する前に、新しいオブジェクトを作成し、バリアントの内容をそのオブジェクトにコピーします。  オブジェクトへの参照がマネージ関数に渡されます。ここで、オブジェクトを自由に変更できます。  呼び出しから制御が返されるときに、参照先オブジェクトが変更されている場合には、その内容が元のバリアントに反映されます。  オブジェクトの型が、呼び出しに渡されたオブジェクトの型と異なる場合、元のバリアントの型が変更され、値がそのバリアントに反映されます。  ここでも、呼び出しに渡されたバリアントの型が、呼び出しから返されるバリアントの型と異なることがあります。  
  
 **VT\_BYREF フラグの設定によるバリアントのマーシャリングの既定の動作**  
  
-   マネージ コードに参照渡しするバリアントには、**VT\_BYREF** フラグを設定することによって、そのバリアントが値ではなく参照を含むことを指定できます。  この場合でも、バリアントは値渡しされるため、バリアントは依然としてオブジェクトへとマーシャリングされます。  呼び出しを実行する前に、マーシャラーは自動的にバリアントの内容を逆参照し、その内容を新しく作成されるオブジェクトへとコピーします。  次に、そのオブジェクトがマネージ関数に渡されます。ただし、呼び出しから制御が返されるときに、このオブジェクトの内容は元のバリアントには反映されません。  マネージ オブジェクトに対する変更内容は失われます。  
  
    > [!CAUTION]
    >  バリアントに **VT\_BYREF** フラグが設定されていても、そのバリアントが値渡しされた場合、その値を変更する方法はありません。  
  
-   マネージ コードに参照渡しするバリアントについても、**VT\_BYREF** フラグを設定することで、バリアントが別の参照を含むことを指定できます。  このようにすると、バリアントは参照渡しされるため、**ref** オブジェクトにマーシャリングされます。  呼び出しを実行する前に、マーシャラーは自動的にバリアントの内容を逆参照し、その内容を新しく作成されるオブジェクトへとコピーします。  呼び出しから制御が返されるときに、オブジェクトの値が元のバリアントに含まれる参照に反映されるのは、そのオブジェクトの型が呼び出しに渡されたオブジェクトの型と同じ場合に限られます。  つまり、反映によって **VT\_BYREF** フラグが設定されたバリアントの型が変更されることはありません。  呼び出しの間にオブジェクトの型が変更された場合、呼び出しから制御が返されるときに <xref:System.InvalidCastException> が発生します。  
  
 バリアントとオブジェクトに関する反映規則を次の表にまとめます。  
  
|変換前|目的|変更内容の反映|  
|---------|--------|-------------|  
|**Variant**  *v*|**Object**  *o*|なし|  
|**Object**  *o*|**Variant**  *v*|なし|  
|**Variant**   ***\****  *pv*|**Ref Object**  *o*|常時|  
|**Ref object**  *o*|**Variant**   ***\****  *pv*|常時|  
|**Variant**  *v* **\(VT\_BYREF** *&#124;*  **VT\_\*\)**|**Object**  *o*|なし|  
|**Variant**  *v* **\(VT\_BYREF** *&#124;*  **VT\_\)**|**Ref Object**  *o*|型が変更されていない場合にだけ反映|  
  
## 参照  
 [既定のマーシャリングの動作](../../../docs/framework/interop/default-marshaling-behavior.md)   
 [Blittable 型と非 Blittable 型](../../../docs/framework/interop/blittable-and-non-blittable-types.md)   
 [Directional Attributes](http://msdn.microsoft.com/ja-jp/241ac5b5-928e-4969-8f58-1dbc048f9ea2)   
 [コピーと固定](../../../docs/framework/interop/copying-and-pinning.md)