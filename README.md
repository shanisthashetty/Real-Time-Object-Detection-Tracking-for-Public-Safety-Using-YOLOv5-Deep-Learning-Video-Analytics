<h1>🎥 Real-Time Object Detection & Tracking for Public Safety<br>Using YOLOv5, Deep Learning & Video Analytics</h1>

<h3>Master’s Thesis </h3>

<p>
This repository contains the full implementation of my Master’s thesis project focused on <b>real-time object detection and analytics</b> using <b>YOLOv5</b>, <b>deep learning</b>, and <b>computer vision</b>.  
The goal is to develop an automated video surveillance system capable of detecting and analyzing objects in traffic footage to support <b>public safety, traffic monitoring, and intelligent transportation systems</b>.
</p>

<br>

<h2>📌 Project Overview</h2>

<p>
The project processes real highway traffic footage and uses <b>YOLOv5</b> to detect multiple objects such as:
</p>

<ul>
  <li>🚗 Cars</li>
  <li>🚚 Trucks</li>
  <li>🚌 Buses</li>
  <li>🚶‍♂️ Pedestrians</li>
</ul>

<p>
It generates:
</p>

<ul>
  <li>🎞 Annotated output video with bounding boxes</li>
  <li>📈 Frame-by-frame detection trend plots</li>
  <li>📊 Aggregated metrics for per-class detection</li>
  <li>🖼 Sample visualizations of processed frames</li>
</ul>

<p>
All implementation details are based on the code in <b>software_file_final.py</b> :contentReference[oaicite:1]{index=1}.
</p>

<br>

<h2>📁 Repository Contents</h2>

<table>
  <tr><th>File</th><th>Description</th></tr>

  <tr>
    <td><b>software_file_final.py</b></td>
    <td>Full video processing pipeline (YOLOv5 loading, inference, analytics, plotting).</td>
  </tr>

  <tr>
    <td><b>software_file_final.ipynb</b></td>
    <td>Notebook version used during development (Google Colab).</td>
  </tr>

  <tr>
    <td><b>british_highway_traffic.mp4</b></td>
    <td>Input test video used for detection.</td>
  </tr>

  <tr>
    <td><b>annotated_output.mp4</b></td>
    <td>YOLOv5 processed video with bounding boxes.</td>
  </tr>

  <tr>
    <td><b>object_counts_plot.png</b></td>
    <td>Frame-wise detection trend visualization.</td>
  </tr>

  <tr>
    <td><b>total_detections_bar.png</b></td>
    <td>Overall detection summary plot.</td>
  </tr>

  <tr>
    <td><b>README.md</b></td>
    <td>Documentation (this file).</td>
  </tr>

</table>

<br>

<h2>🧠 System Workflow</h2>

<p>The detection workflow includes:</p>

<ol>
  <li><b>Load YOLOv5 model</b> via Torch Hub</li>
  <li><b>Read input video</b> frame by frame</li>
  <li><b>Run inference</b> on each frame</li>
  <li><b>Render bounding boxes</b> and labels</li>
  <li><b>Write annotated frames</b> into a new output video</li>
  <li><b>Track object counts</b> across all frames</li>
  <li><b>Generate plots</b> for class frequencies and trends</li>
</ol>

<br>

<h2>💻 Code Implementation (High-Level)</h2>

<p>
The core logic (detection, analytics, plotting) is implemented in <code>software_file_final.py</code> :contentReference[oaicite:2]{index=2}.
</p>

<h3>📥 1. Load YOLOv5</h3>

<pre><code>
model = torch.hub.load('ultralytics/yolov5', 'yolov5s', force_reload=True)
</code></pre>

<h3>🎞 2. Process Video Frames</h3>

<pre><code>
cap = cv2.VideoCapture('british_highway_traffic.mp4')
results = model(frame)
results.render()   # overlay bounding boxes
</code></pre>

<h3>📊 3. Track Object Counts</h3>

<pre><code>
for cls in ['person', 'car', 'truck', 'bus']:
    object_counts[cls].append(count_per_class.get(cls, 0))
</code></pre>

<h3>📈 4. Generate Detection Trend Plots</h3>

<pre><code>
plt.plot(frame_counts, object_counts[cls], label=cls)
</code></pre>

<h3>🖼 5. Visualize Sample Frames</h3>

<pre><code>
cv2_imshow(processed_frames[i])
</code></pre>

<br>

<h2>📊 Evaluation & Metrics</h2>

<p>The system reports:</p>

<ul>
  <li><b>Total detections per class</b></li>
  <li><b>Average detections per frame</b></li>
  <li><b>Temporal detection patterns</b></li>
  <li><b>Peak and low-activity intervals</b></li>
</ul>

<h3>Example Output:</h3>

<pre><code>
📊 Evaluation Metrics:
Car      → Total: 542  | Avg per frame: 3.21
Truck    → Total: 128  | Avg per frame: 0.75
Bus      → Total: 44   | Avg per frame: 0.20
Person   → Total: 11   | Avg per frame: 0.02
</code></pre>

<br>

<h2>📈 Visual Results</h2>

<ul>
  <li><b>object_counts_plot.png</b> — Frame-by-frame detection trend</li>
  <li><b>total_detections_bar.png</b> — Total detection summary</li>
  <li><b>annotated_output.mp4</b> — Final YOLOv5 analyzed video</li>
</ul>

<br>

<h2>🎯 Applications</h2>

<ul>
  <li>🚦 Intelligent Traffic Monitoring</li>
  <li>📉 Accident & congestion detection</li>
  <li>🚓 Public safety surveillance</li>
  <li>🧭 Urban planning & infrastructure development</li>
  <li>📡 Real-time analytics systems</li>
</ul>

<br>

<h2>🛠 Tools &amp; Technologies</h2>

<ul>
  <li>YOLOv5</li>
  <li>PyTorch</li>
  <li>OpenCV</li>
  <li>NumPy</li>
  <li>Matplotlib</li>
  <li>Google Colab</li>
  <li>Python 3.x</li>
</ul>

<br>

<h2>🚀 How to Run the Project</h2>

<h3>1️⃣ Install Dependencies</h3>

<pre><code>
pip install torch torchvision torchaudio
pip install opencv-python matplotlib numpy
</code></pre>

<h3>2️⃣ Run Detection Script</h3>

<pre><code>
python software_file_final.py
</code></pre>

<h3>3️⃣ Outputs Generated</h3>

<ul>
  <li><code>annotated_output.mp4</code></li>
  <li><code>object_counts_plot.png</code></li>
  <li><code>total_detections_bar.png</code></li>
</ul>

<br>

<h2>🏁 Conclusion</h2>

<p>
This thesis demonstrates how <b>deep learning</b> and <b>real-time video analytics</b> can enhance public safety and traffic systems.  
YOLOv5 proves to be fast, lightweight, and accurate for real-time detection.  
The system provides foundational work for advanced tracking, anomaly detection, and smart-city surveillance solutions.
</p>

<br>

<h2>⭐ Summary</h2>

<ul>
  <li>✔ Real-time video analytics pipeline</li>
  <li>✔ YOLOv5-based object detection</li>
  <li>✔ Automated plotting & performance metrics</li>
  <li>✔ Public safety & traffic monitoring applications</li>
</ul>
