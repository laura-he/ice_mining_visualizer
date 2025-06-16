## Running the Interactive Visualizer

We use Phoenix to interactively visualize the embedding space in 3D. We recommend installing Phoenix on your laptop, or a machine where you can SSH with X11 forwardning, in order to visualize the results.

**Requirements**
0. Install Conda
1. Create a new conda environment:
   ```bash
   conda create -n phoenix
   ```

   And activate the environment:
   ```bash
   conda activate phoenix
   ```
2. Install the requirements:

   Using Conda:
   ```bash
   conda env update -f environment.yml
   ```

   Or using pip:
   ```bash
   pip install -r requirements.txt
   ```

3. You will need 2 files in order to perform the visualization:
   1. ```data_for_export.parquet.zip```, containing the metadata and embeddings for each entry in the dataset
   2. ```zipped_thumbnail_images.tar.gz```, containing .jpeg thumbnail images for visualization

4. Unzip the thumbnail images tarball: 
5. To connect images to the locahost and keep it running in the background, open a new terminal, change directory to ```thumbnail_images```, and run the following command:
   ```bash
   python -m http.server 7000
   ```
   The images will be hosted on port number ```7000```.
   
6. Open another terminal window. From the directory where the code exists, run the following:
   ```bash
   python visualizer.py <path_to_zip_file> --port 7000 --which-embedding umap
   ```
   This will launch the visualization script, using the thumbnail images that we just un-tarred, on the port that we specified above.

If the last step succeeds, you will see outputs like this:
```bash
                                          embeddings  
0  [-0.07116878777742386, -0.02092127315700054, 0...  
1  [0.03098396770656109, -0.012207355350255966, 0...  
2  [-0.001951615558937192, -0.059190645813941956,...  
3  [0.04287125542759895, 0.055738892406225204, -0...  
4  [-0.03130991384387016, -0.024252604693174362, ...  
🌍 To view the Phoenix app in your browser, visit http://localhost:54116/
📺 To view the Phoenix app in a notebook, run `px.active_session().view()`
📖 For more information on how to use Phoenix, check out https://docs.arize.com/phoenix
```

You should now be able to access the interactive session by visiting ```http://localhost:54116/```.
