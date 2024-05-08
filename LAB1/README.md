    We will generate a per-pixel boundary score. We will start from a bare bone edge detector that simply uses the gradient magnitude as the boundary score. We will add non-maximum suppression, image smoothing, and optionally additional bells and whistles. We have provided some starter code, images from the BSDS dataset and evaluation code. Note that we are using a faster approximate version of the evaluation code, so metrics here won't be directly comparable to ones reported in papers.
    <div align="center">
    <img src="contours/227092.jpg" width="30%">
    <img src="contours/227092-raw.png" width="30%">
    <img src="contours/227092-nms.png" width="30%">
    </div>

    1. **[0 pts] Preliminaries.** We have implemented a contour detector that uses the magnitude of the local image gradient as the boundary score. This gives us overall max F-score, average max F-score and AP of 0.52, 0.56, 0.43 respectively. Reproduce these results by running [contours/contour_demo.py](contours/contour_demo.py). Confirm your setup by matching these results. When you run `contour_demo.py`, it saves the output contours in the folder `contours/output/demo`, prints out the 3 metrics, and produces a precision-recall (pr) plots at `contours/output/demo/pr.pdf`. Overall max F-score is the most important metric, but we will look at all three. For the next parts you have to change the code inside `contour_solve.py` and set output directory for each implementation, for instance `python3 contour_demo.py --output_dir output/part1` will produce the results and PR plot in `output/part1` directory.

    2.  **[2 pts] Warm-up.** As you visualize the produced edges, you will notice artifacts at image boundaries. Modify how the convolution is being done to minimize these artifacts.

    3.  **[5 pts] Smoothing.** Next, notice that we are using [−1, 0, 1] filters for computing the gradients, and they are susceptible to noise. Use derivative of Gaussian filters to obtain more robust estimates of the gradient. Experiment with different sigma for this Gaussian filtering and pick the one that works the best.
    
    4.  **[8 pts] Non-maximum Suppression.** The current code does not produce thin edges. Implement non-maximum suppression, where we look at the gradient magnitude at the two neighbours in the direction perpendicular to the edge. We suppress the output at the current pixel if the output at the current pixel is not more than at the neighbors. You will have to compute the orientation of the contour (using the X and Y gradients), and implement interpolation to lookup values at the neighbouring pixels.
    5. **[10 pts] SIFT ** In Pysift directory there is a pysift.py file. There search for TODO and replace that by code
    
    
