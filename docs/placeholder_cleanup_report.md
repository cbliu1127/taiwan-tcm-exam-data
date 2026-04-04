# Placeholder Cleanup Report

This report summarizes the 60 questions that originally still had `?????` option placeholders and how they were resolved.

- Total fixed questions: 60
- Image option mapping: 48
- Text/OCR recovery: 12

## What Happened

- Image option mapping: the source question already used image-based options, but the earlier pipeline only extracted detached figure fragments or split one option into multiple pieces. As a result, A-D could not be assigned reliably, so the JSON kept `?????`.
- Text/OCR recovery: the earlier OCR or segmentation pass failed to recover usable option text, usually on count-style options such as `1/2/3/4`, `14/15/16/17`, or one anatomy-label question. These were re-read from the source PDF or rendered page image and written back into `exam.json`.

## Fixed Question List

### Image option mapping

- `101_1_1_2`: q40, 42, 43, 46, 47, 48, 50, 51, 53
- `101_2_1_2`: q66, 67, 75, 76, 78, 79, 80
- `101_2_2_3`: q56, 63
- `102_1_1_2`: q40, 42, 43, 44, 45, 46, 50, 51, 53, 54, 55
- `102_2_1_2`: q6, 40, 50, 51, 60, 65, 77, 78, 79, 80
- `103_1_1_2`: q69, 73, 74, 78, 80
- `103_2_1_2`: q11, 12
- `104_1_1_2`: q41
- `104_2_1_2`: q49

### Text/OCR recovery

- `102_2_2_4`: q41
- `103_2_1_1`: q19, 55
- `103_2_1_2`: q14, 19
- `104_1_1_2`: q11, 14, 18, 26, 27, 33
- `104_1_2_3`: q37

## Final Status

- Remaining `?????` options: 0
- The last 6 image-option cases were fixed by cropping A-D directly from the original question image instead of relying on broken figure fragments.
- The last 12 text cases were filled from the PDF text layer or the rendered page image and then written back into `exam.json`.
