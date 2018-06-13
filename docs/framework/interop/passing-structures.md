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
# <a name="passing-structures"></a><span data-ttu-id="68c1d-102">構造体の受け渡し</span><span class="sxs-lookup"><span data-stu-id="68c1d-102">Passing Structures</span></span>
<span data-ttu-id="68c1d-103">多くのアンマネージ関数では、構造体のメンバー (Visual Basic ではユーザー定義型) またはマネージ コードで定義されたクラスのメンバーがパラメーターとして渡されることを期待しています。</span><span class="sxs-lookup"><span data-stu-id="68c1d-103">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="68c1d-104">プラットフォーム呼び出しを使って構造体またはクラスをアンマネージ コードに渡す場合は、元のレイアウトやアラインメントを保持するための追加情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68c1d-104">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="68c1d-105">このトピックでは、フォーマットされた型を定義するために使用する <xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="68c1d-105">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="68c1d-106">マネージ構造体やマネージ クラスの場合は、**LayoutKind** 列挙型によって提供される想定されたレイアウト動作から選択できます。</span><span class="sxs-lookup"><span data-stu-id="68c1d-106">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="68c1d-107">ここで説明する概念の中心は、構造体の型とクラスの型の相違点です。</span><span class="sxs-lookup"><span data-stu-id="68c1d-107">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="68c1d-108">構造体は値型であり、クラスは参照型です。クラスは常に最低 1 つのレベルのメモリの間接参照 (値へのポインター) を提供します。</span><span class="sxs-lookup"><span data-stu-id="68c1d-108">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="68c1d-109">アンマネージ関数は、次の表の第 1 列のシグネチャに示されているように、間接参照を必要とすることが多いため、この違いは重要です。</span><span class="sxs-lookup"><span data-stu-id="68c1d-109">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="68c1d-110">他の列のマネージ構造体およびマネージ クラスの宣言は、宣言でどの程度間接参照のレベルを調整できるかを示しています。宣言は、Visual Basic と Visual C# の両方で指定されています。</span><span class="sxs-lookup"><span data-stu-id="68c1d-110">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="68c1d-111">アンマネージ シグネチャ</span><span class="sxs-lookup"><span data-stu-id="68c1d-111">Unmanaged signature</span></span>|<span data-ttu-id="68c1d-112">マネージ宣言</span><span class="sxs-lookup"><span data-stu-id="68c1d-112">Managed declaration:</span></span> <br /><span data-ttu-id="68c1d-113">間接参照なし</span><span class="sxs-lookup"><span data-stu-id="68c1d-113">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="68c1d-114">マネージ宣言</span><span class="sxs-lookup"><span data-stu-id="68c1d-114">Managed declaration:</span></span> <br /><span data-ttu-id="68c1d-115">1 レベルの間接参照</span><span class="sxs-lookup"><span data-stu-id="68c1d-115">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="68c1d-116">0 レベルの間接参照を必要とします。</span><span class="sxs-lookup"><span data-stu-id="68c1d-116">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="68c1d-117">0 レベルの間接参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="68c1d-117">Adds zero levels of indirection.</span></span>|<span data-ttu-id="68c1d-118">既に 1 レベルの間接参照が存在するため調整できません。</span><span class="sxs-lookup"><span data-stu-id="68c1d-118">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="68c1d-119">1 レベルの間接参照を必要とします。</span><span class="sxs-lookup"><span data-stu-id="68c1d-119">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="68c1d-120">1 レベルの間接参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="68c1d-120">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="68c1d-121">0 レベルの間接参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="68c1d-121">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="68c1d-122">2 レベルの間接参照を必要とします。</span><span class="sxs-lookup"><span data-stu-id="68c1d-122">Demands two levels of indirection.</span></span>|<span data-ttu-id="68c1d-123">**ByRef** **ByRef** または `ref` `ref` を使用できないため調整できません。</span><span class="sxs-lookup"><span data-stu-id="68c1d-123">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="68c1d-124">1 レベルの間接参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="68c1d-124">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="68c1d-125">この表は、プラットフォーム呼び出しの宣言について次のようなガイドラインを示しています。</span><span class="sxs-lookup"><span data-stu-id="68c1d-125">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
-   <span data-ttu-id="68c1d-126">アンマネージ関数が間接参照を必要としない場合は、値渡しによる構造体を使用します。</span><span class="sxs-lookup"><span data-stu-id="68c1d-126">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
-   <span data-ttu-id="68c1d-127">アンマネージ関数が 1 レベルの間接参照を必要とする場合は、参照渡しによる構造体または値渡しによるクラスのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="68c1d-127">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
-   <span data-ttu-id="68c1d-128">アンマネージ関数が 2 レベルの間接参照を必要とする場合は、参照渡しによるクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="68c1d-128">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="68c1d-129">構造体の宣言と受け渡し</span><span class="sxs-lookup"><span data-stu-id="68c1d-129">Declaring and Passing Structures</span></span>  
 <span data-ttu-id="68c1d-130">マネージ コードで `Point` 型および `Rect` 型を定義し、これらの型を User32.dll ファイル内の **PtInRect** 関数にパラメーターとして渡す方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="68c1d-130">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="68c1d-131">**PtInRect** は、次に示すアンマネージ シグネチャを持っています。</span><span class="sxs-lookup"><span data-stu-id="68c1d-131">**PtInRect** has the following unmanaged signature:</span></span>  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="68c1d-132">この関数は RECT 型へのポインターを期待しているため、Rect 構造体は参照渡しする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="68c1d-132">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
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
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="68c1d-133">クラスの宣言と受け渡し</span><span class="sxs-lookup"><span data-stu-id="68c1d-133">Declaring and Passing Classes</span></span>  
 <span data-ttu-id="68c1d-134">クラスが固定したメンバー レイアウトを持っている場合に限り、クラスのメンバーをアンマネージ DLL 関数に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="68c1d-134">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="68c1d-135">定義の順序で固定されている `MySystemTime` クラスのメンバーを User32.dll ファイル内の **GetSystemTime** に渡す方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="68c1d-135">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="68c1d-136">**GetSystemTime** は、次に示すアンマネージ シグネチャを持っています。</span><span class="sxs-lookup"><span data-stu-id="68c1d-136">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="68c1d-137">値型とは異なり、クラスは常に 1 レベルの間接参照を使用します。</span><span class="sxs-lookup"><span data-stu-id="68c1d-137">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="68c1d-138">参照</span><span class="sxs-lookup"><span data-stu-id="68c1d-138">See Also</span></span>  
 [<span data-ttu-id="68c1d-139">DLL 関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="68c1d-139">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
