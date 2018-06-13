---
title: 構造体の受け渡し
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3764916263f6f88615d61badaf2c32807bcc09b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391509"
---
# <a name="passing-structures"></a>構造体の受け渡し
多くのアンマネージ関数では、構造体のメンバー (Visual Basic ではユーザー定義型) またはマネージ コードで定義されたクラスのメンバーがパラメーターとして渡されることを期待しています。 プラットフォーム呼び出しを使って構造体またはクラスをアンマネージ コードに渡す場合は、元のレイアウトやアラインメントを保持するための追加情報を提供する必要があります。 このトピックでは、フォーマットされた型を定義するために使用する <xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性について説明します。 マネージ構造体やマネージ クラスの場合は、**LayoutKind** 列挙型によって提供される想定されたレイアウト動作から選択できます。  
  
 ここで説明する概念の中心は、構造体の型とクラスの型の相違点です。 構造体は値型であり、クラスは参照型です。クラスは常に最低 1 つのレベルのメモリの間接参照 (値へのポインター) を提供します。 アンマネージ関数は、次の表の第 1 列のシグネチャに示されているように、間接参照を必要とすることが多いため、この違いは重要です。 他の列のマネージ構造体およびマネージ クラスの宣言は、宣言でどの程度間接参照のレベルを調整できるかを示しています。宣言は、Visual Basic と Visual C# の両方で指定されています。  
  
|アンマネージ シグネチャ|マネージ宣言 <br />間接参照なし<br />`Structure MyType`<br />`struct MyType;`|マネージ宣言 <br />1 レベルの間接参照<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> 0 レベルの間接参照を必要とします。|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> 0 レベルの間接参照を追加します。|既に 1 レベルの間接参照が存在するため調整できません。|  
|`DoWork(MyType* x);`<br /><br /> 1 レベルの間接参照を必要とします。|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> 1 レベルの間接参照を追加します。|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> 0 レベルの間接参照を追加します。|  
|`DoWork(MyType** x);`<br /><br /> 2 レベルの間接参照を必要とします。|**ByRef** **ByRef** または `ref` `ref` を使用できないため調整できません。|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> 1 レベルの間接参照を追加します。|  
  
 この表は、プラットフォーム呼び出しの宣言について次のようなガイドラインを示しています。  
  
-   アンマネージ関数が間接参照を必要としない場合は、値渡しによる構造体を使用します。  
  
-   アンマネージ関数が 1 レベルの間接参照を必要とする場合は、参照渡しによる構造体または値渡しによるクラスのいずれかを使用します。  
  
-   アンマネージ関数が 2 レベルの間接参照を必要とする場合は、参照渡しによるクラスを使用します。  
  
## <a name="declaring-and-passing-structures"></a>構造体の宣言と受け渡し  
 マネージ コードで `Point` 型および `Rect` 型を定義し、これらの型を User32.dll ファイル内の **PtInRect** 関数にパラメーターとして渡す方法の例を次に示します。 **PtInRect** は、次に示すアンマネージ シグネチャを持っています。  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 この関数は RECT 型へのポインターを期待しているため、Rect 構造体は参照渡しする必要があることに注意してください。  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
    Public x As Integer  
    Public y As Integer  
End Structure  
  
Public Structure <StructLayout(LayoutKind.Explicit)> Rect  
    <FieldOffset(0)> Public left As Integer  
    <FieldOffset(4)> Public top As Integer  
    <FieldOffset(8)> Public right As Integer  
    <FieldOffset(12)> Public bottom As Integer  
End Structure  
  
Class Win32API      
    Declare Auto Function PtInRect Lib "user32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
    public int x;  
    public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
    [FieldOffset(0)] public int left;  
    [FieldOffset(4)] public int top;  
    [FieldOffset(8)] public int right;  
    [FieldOffset(12)] public int bottom;  
}     
  
class Win32API {  
    [DllImport("User32.dll")]  
    public static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a>クラスの宣言と受け渡し  
 クラスが固定したメンバー レイアウトを持っている場合に限り、クラスのメンバーをアンマネージ DLL 関数に渡すことができます。 定義の順序で固定されている `MySystemTime` クラスのメンバーを User32.dll ファイル内の **GetSystemTime** に渡す方法の例を次に示します。 **GetSystemTime** は、次に示すアンマネージ シグネチャを持っています。  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 値型とは異なり、クラスは常に 1 レベルの間接参照を使用します。  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
Imports Microsoft.VisualBasic  
  
<StructLayout(LayoutKind.Sequential)> Public Class MySystemTime  
    Public wYear As Short  
    Public wMonth As Short  
    Public wDayOfWeek As Short   
    Public wDay As Short  
    Public wHour As Short  
    Public wMinute As Short  
    Public wSecond As Short  
    Public wMiliseconds As Short  
End Class  
  
Public Class Win32  
    Declare Auto Sub GetSystemTime Lib "Kernel32.dll"(sysTime _  
        As MySystemTime)  
    Declare Auto Function MessageBox Lib "User32.dll"(hWnd As IntPtr, _  
        txt As String, caption As String, Typ As Integer) As Integer  
End Class  
  
Public Class TestPlatformInvoke      
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        Win32.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        Win32.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)        
    End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class MySystemTime {  
    public ushort wYear;   
    public ushort wMonth;  
    public ushort wDayOfWeek;   
    public ushort wDay;   
    public ushort wHour;   
    public ushort wMinute;   
    public ushort wSecond;   
    public ushort wMilliseconds;   
}  
class Win32API {  
    [DllImport("Kernel32.dll")]  
    public static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet=CharSet.Auto)]  
     public static extern int MessageBox(IntPtr hWnd,  
         string text, string caption, int options);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        Win32API.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        Win32API.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a>参照  
 [DLL 関数の呼び出し](../../../docs/framework/interop/calling-a-dll-function.md)  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
