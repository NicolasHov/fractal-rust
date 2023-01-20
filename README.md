# fractal-rust

Cool example for usage of a thread pool: one thread for each pixel.

I took it from https://rust-lang-nursery.github.io/rust-cookbook/concurrency/threads.html#draw-fractal-dispatching-work-to-a-thread-pool 

## Steps:

* Allocate memory for output image of given width and height with ImageBuffer::new. 

* Rgb::from_channels calculates RGB pixel values. 

* Create ThreadPool with thread count equal to number of cores with num_cpus::get. 

* ThreadPool::execute receives each pixel as a separate job.

* mpsc::channel receives the jobs and Receiver::recv retrieves them. 

* ImageBuffer::put_pixel uses the data to set the pixel color. 

* ImageBuffer::save writes the image to output.png.
