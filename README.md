*This project has been created as part of the 42 curriculum by scamlett.*

# Python Module 05: Code Nexus Data Pipeline

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)
![42](https://img.shields.io/badge/42-Málaga-000000)

## Description

A three-step project that builds a small data pipeline using abstract
classes and polymorphism. Different kinds of data (numbers, text, log
entries) each get their own processor, a stream routes every item to the
processor that accepts it, and export plugins write the results out.

| Exercise | File | Topic |
|----------|------|-------|
| ex0 | `data_processor.py` | An abstract `DataProcessor` base class with `NumericProcessor`, `TextProcessor` and `LogProcessor` |
| ex1 | `data_stream.py` | A `DataStream` that holds registered processors and sends each item to the one whose `validate()` accepts it |
| ex2 | `data_pipeline.py` | Export plugins (`CSVExportPlugin`, `JSONExportPlugin`) described by a `Protocol` |

```
mixed data ──► DataStream ──► NumericProcessor ─┐
                         ├──► TextProcessor ────┼──► ExportPlugin (CSV / JSON)
                         └──► LogProcessor ─────┘
```

## Instructions

```bash
python3 ex0/data_processor.py
python3 ex1/data_stream.py
python3 ex2/data_pipeline.py
```

## What I learned

- `abc.ABC` and `@abstractmethod`: a base class can force every subclass to
  implement `validate()` and `ingest()`, and cannot be instantiated itself
- Polymorphism: the stream calls the same methods on every processor without
  caring which kind it is
- `typing.Protocol` for "anything with a `process_output()` method", which
  describes a shape instead of requiring inheritance
- Union types like `int | float | list[int | float]` to describe what a
  method accepts
- Splitting a program into small, swappable pieces that each do one job
