# SimpleConsoleProgress

Free and open-source library with a simple progress indicator for .NET console projects.

[![Build Status](https://filipliwinski.visualstudio.com/SimpleConsoleProgress/_apis/build/status/SimpleConsoleProgress?branchName=master)](https://filipliwinski.visualstudio.com/SimpleConsoleProgress/_build/latest?definitionId=2&branchName=master)
[![CodeQL](https://github.com/filipliwinski/SimpleConsoleProgress/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/filipliwinski/SimpleConsoleProgress/actions/workflows/codeql-analysis.yml)

Support for .NET Framework (4.5+), .NET Core and .NET 5.

Download from [NuGet](https://www.nuget.org/packages/SimpleConsoleProgress/).

[![NuGet](https://img.shields.io/nuget/v/SimpleConsoleProgress.svg)](https://www.nuget.org/packages/SimpleConsoleProgress/)
[![NuGet](https://img.shields.io/nuget/dt/SimpleConsoleProgress.svg)](https://www.nuget.org/packages/SimpleConsoleProgress/) 

## How to use

    using SimpleConsoleProgress;

### Single-line progress bar

Progress bar is updating in a single line. Use it if the progress is the only output in the process.

<img src="./assets/img/singleLine.gif?raw=true"/>

    var total = 20;
    for (int i = 0; i < total; i++)
    {
        ProgressBar.Write(i, total);
    }
    Console.WriteLine("Process completed.");

### Multiline progress bar

Each progress update is written on a new line.

<img src="./assets/img/multiline.gif?raw=true"/>

    var total = 20;
    for (int i = 0; i < total; i++)
    {
        ProgressBar.WriteLine(i, total);
    }
    Console.WriteLine("Process completed.");

### Options

#### Show elapsed time

You can provide a `TimeSpan` object with the time to show next to the progress bar. SimpleConsoleProgress does not include any timers, to be as simple as possible.

<img src="./assets/img/elapsedTime.gif?raw=true"/>

    var total = 20;
    var timer = new Stopwatch();
    timer.Start();
    for (int i = 0; i < total; i++)
    {
        ProgressBar.Write(i, total, timer.Elapsed);
    }
    Console.WriteLine("Process completed.");

#### Custom progress indicator

By default, '#' is used as a progress indicator. You can change it with any character you want.

<img src="./assets/img/customIndicator.gif?raw=true"/>

    var total = 20;
    for (int i = 0; i < total; i++)
    {
        ProgressBar.Write(i, total, character: '>');
    }
    Console.WriteLine("Process completed.");

#### Autohide progress bar (single-line)

By default, single-line progress bar persists in the output. You can hide it when it completes.

<img src="./assets/img/autoHide.gif?raw=true"/>

    var total = 20;
    for (int i = 0; i < total; i++)
    {
        ProgressBar.Write(i, total, autoHide: true);
    }
    Console.WriteLine("Process completed.");

#### Percent value location

The current percentage is displayed by default in the middle of the progress bar. It can be on the left / right side of the progress bar or it can be hidden.

##### Location - left

<img src="./assets/img/location-left.gif?raw=true"/>

    var total = 20;
    for (int i = 0; i < total; i++)
    {
        ProgressBar.Write(i, total, location: PercentLocation.Left);
    }
    Console.WriteLine("Process completed.");

##### Location - right

<img src="./assets/img/location-right.gif?raw=true"/>

    var total = 20;
    for (int i = 0; i < total; i++)
    {
        ProgressBar.Write(i, total, location: PercentLocation.Right);
    }
    Console.WriteLine("Process completed.");

##### Location - none

<img src="./assets/img/location-none.gif?raw=true"/>

    var total = 20;
    for (int i = 0; i < total; i++)
    {
        ProgressBar.Write(i, total, location: PercentLocation.None);
    }
    Console.WriteLine("Process completed.");

#### Accuracy

By default, integer values are displayed. You can increase the accuracy to three decimal places.

##### Accuracy - one decimal place 

<img src="./assets/img/accuracy-1.gif?raw=true"/>

    var total = 20;
    for (int i = 0; i < total; i++)
    {
        ProgressBar.Write(i, total, accuracy: 1);
    }
    Console.WriteLine("Process completed.");

##### Accuracy - two decimal places

<img src="./assets/img/accuracy-2.gif?raw=true"/>

    var total = 20;
    for (int i = 0; i < total; i++)
    {
        ProgressBar.Write(i, total, accuracy: 2);
    }
    Console.WriteLine("Process completed.");

##### Accuracy - three decimal places

<img src="./assets/img/accuracy-3.gif?raw=true"/>

    var total = 20;
    for (int i = 0; i < total; i++)
    {
        ProgressBar.Write(i, total, accuracy: 3);
    }
    Console.WriteLine("Process completed.");
